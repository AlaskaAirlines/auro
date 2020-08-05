# Lessons learned from building Tealium component

The purpose of this document is to leave us breadcrumbs of our approach in case something changes down the road or we look at doing this again, we know what we have tried.

## The original code snippet that set us on this path

```javascript
<auro-hyperlink id="baggageModalHyperlink" href="#">Baggage fees</auro-hyperlink> may apply.
<script>
  document.querySelector("#baggageModalHyperlink").addEventListener('click', function (event) {
    event.preventDefault();
    if (utag_data) {
      var trackingInfo = utag_data['page_name'] + ' : baggage charges';
      if (typeof (utag) != 'undefined') {
        utag.link({ 'event_name': 'link_click', 'link_tracking': trackingInfo });
      }
    }
    showBaggageCharges($(this));
  }
</script>
```

## Our idea for a possible usage

We started off with the idea of creating an auro-tealium component to abstract away as much of the data collection process as possible. The idea was to have this component wrapped around anything you wanted tagged and provide some details in the attributes like this:

```javascript
<auro-tealium>
  <auro-hyperlink id="baggageModalHyperlink" href="#">Baggage fees</auro-hyperlink>
</auro-tealium> may apply.
```

## The web component to support the use case

We discovered through this process that Tealium requires their universal tagging javascript library to be loaded right after the opening `<body>` tag, which puts the `utag` object in the global javascript for the page. In order for our web component to use the utag object, it needed to be passed into the component. The other piece that we found we needed was to provide a callback function when a button or hyperlink was clicked in some of our use cases. One of the limitations of web components is that attributes in the element are only passes as strings, so you cannot pass a function or object in as an attribute, leaving us with writing more javascript to update the element in the DOM.

This is the code we put together. It would find all the children of the `auro-tealium` component and attach a click event handler on it.
```javascript
import { LitElement, html } from "lit-element";

// Import touch detection lib
import "focus-visible/dist/focus-visible.min.js";

// build the component class
class AuroTealium extends LitElement {
  // constructor() {
  //   super();
  // }

  // function to define props used within the scope of thie component
  static get properties() {
    return {
      trackingInfo:   { type: String },
      utag: { type: Object },
      callback: { type: Function }
    };
  }

  initializeClickHandler() {
    const children = Array.from(this.children);

    children.forEach((child) => {
      child.trackingInfo = this.trackingInfo;
      child.utag = this.utag;
      child.callback = this.callback;
      child.addEventListener('click', this.handleLinkClick);
    });
  }

  handleLinkClick(event) {
    event.preventDefault();
    if (event.target.trackingInfo && typeof event.target.utag !== 'undefined') {
      console.log(event.target.trackingInfo);
      event.target.utag.link({
          'event_name': 'link_click',
          'link_tracking': this.trackingInfo
        });
    }
    event.target.callback(event.target);
  }

  // function that renders the HTML and CSS into  the scope of the component
  render() {
    return html`
      <div>
        <slot></slot>
      </div>
    `;
  }
}

/* istanbul ignore else */
// define the name of the custom component
if (!customElements.get("auro-tealium")) {
  customElements.define("auro-tealium", AuroTealium);
}
```

## How it really turned out

We ended up creating the `initializeClickHander()` function because we needed to pass the parameters to the child components in order for the click handler to use them, like the callback function. Referencing `this` in the handler function referenced the target of the event, not the `auro-tealium` component.

Here is how we ended up consuming the component. Notice that not only did we have to use that element, but we had to give it an ID so we could follow it up with a global script to set the properties inside the component and call the initialize function we created.
```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    <script type="module" src="../src/auro-tealium.js"></script>
  </head>
  <body>
    <!-- Tealium Universal Tag -->
    <script type="text/javascript">
      (function(a,b,c,d) {
        a='//tags.tiqcdn.com/utag/alaska/main/dev/utag.js';
        b=document;c='script';d=b.createElement(c);d.src=a;
        d.type='text/java'+c;d.async=true;
        a=b.getElementsByTagName(c)[0];a.parentNode.insertBefore(d,a)})();
    </script>
    ...
    <auro-tealium id="demo1" trackingInfo="Click Button Info">
      <button>Click Me!</button>
    </auro-tealium>
    <script type="module">
      let el = document.getElementById("demo1");
      el.callback = (target) => {
        console.log("Callback Function Fired");
      };
      el.utag = utag;
      el.initializeClickHandler();
    </script>
  </body>
```

## Conclusion

After all this digging and putting this together, we have reached the conclusion that this provides no value to the engineers to add tagging to components. Most of the work is done in the global javascript anyway, so the web component doesn't provide much value here. All that work was to abstract away the one call to the link function of `utag`. 