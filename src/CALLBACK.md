# Component JavaScript Callback

![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/ods-docs.svg?color=orange)

When building custom elements with litElement, use lit-html's `@event` binding in the custom element's template, inside the `render()` function to add an event listener.

```javascript
render() {
  return html`<button @click="${this.handleClick}">click</button>`;
}

or

render() {
  return html`<button @click=${this.handleClick}>click</button>`;
}
```

When using litElement custom elements, an event can be bound to the outer component itself, as shown in this React example.

```js
<my-element onClick={() => console.log(`I am bound to the element`)}"></my-element>
```

Used this way, the event will only be bound to the outer HTML container of the custom element, not any element contained within the shadow DOM. This would be like binding a click event to a `div` element wrapping a `button` element contained within.

## Passing event into shadow DOM w/React

When using custom elements in React, the component's API needs to allow for any external event to be bound to the appropriate HTML element contained within the custom element.

React, specifically JSX, will not allow for a string to be passed into the scope fo an `onClick` event, so a reference will need to be created to pass the event into the custom element's `@click` event binding.

In the `constructor()` function, assign the [ref](https://reactjs.org/docs/refs-and-the-dom.html) to an instance property. In this example, `logButton` will be the new ref.

```javascript
constructor(props) {
  super(props);
  this.logButton = React.createRef();
}
```

In the next example, in the `componentDidMount()` function, the current attribute of the ref is bound to a variable. The callback function is bound to the `buttonCallback` prop of the `<ods-button>` API using the ref's current attribute.

```js
componentDidMount() {
  const logButtonEvent = this.logButton.current;
  logButtonEvent.buttonCallback = (e) => console.log(e.target);
}
```

This example shows a `ref` to store a reference to a custom element DOM node:

```html
<ods-button ref={this.logButton}>hello world</ods-button>
```

A full working example of this is as follows:

```javascript
import React, { Component } from 'react';
import './sass/app.scss';
import "@alaskaairux/ods-button/ods-button";

class App extends Component {
  constructor(props) {
    super(props);
    this.logButton = React.createRef();
  }

  render() {
    return (
      <div className="App">
        <header className="App-header">
          <ods-button title='hello button' ref={this.logButton}>hello world</ods-button>
        </header>
      </div>
    );
  }

  componentDidMount() {
    const logButtonEvent = this.logButton.current;
    logButtonEvent.buttonCallback = (e) => console.log(e.target);
  }
}

export default App;
```

##
<footer>
Alaska Airlines Auro Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
