# Why Custom Elements?

**Problem**: Building agnostic HTML/CSS/JS deliverables places much of the onus on the font-end engineers to ensure that they are compliant with the design standard over time. Maintaining versioning is impossible.

**Constraint**: Development teams deserve the right to leverage the technology that best suits their deliverable. A design system deliverable must not place unnecessary bias or be overly opinionated in execution.

**Opportunity**: HTML Custom Elements and the shadow DOM provide a framework agnostic version-able deliverable based on browser standards.

## Topics

* <a href="#strengthsinstandards">Web Components; Strengths in standards</a>
* <a href="#customelements">HTML Custom Elements</a>
* <a href="#shadowdom">Shadow DOM</a>
* <a href="#itsastadndard">It's a standard? But, no frameworks?</a>
* <a href="#aurouseslitelement">Auro uses litElement</a>
* <a href="#resources">Resources</a>

<a id="strengthsinstandards"></a>
## Web Components; Strengths in standards

The strength of the web has its foundation in the maintenance of standards. Looking across the vast spectrum of web technologies, the most widely used tech either was based on standards or help drive the next evolution of current standards.

When building web interfaces, regardless of the tech being used, the more the tech is aligned with HTML, CSS and JS standards, the more chance that the tech will not only be adopted well, but also stand the test of time.

It is our assumption that the emerging standard of Web Components fits square into that opinion statement. With a landslide of new support from all the major browsers, Web Components offer a suite of technologies allowing developers to create reusable custom HTML elements with their functionality encapsulated away from the rest of the app's code.

<a id="customelements"></a>
## HTML Custom Elements

HTML Custom Elements is a set of JavaScript APIs that allow developers to construct custom HTML elements and their behavior.

HTML Custom Elements v1.0 are currently part of the [W3C Standard](https://www.w3.org/TR/custom-elements/) as well the [HTML Living Standard](https://html.spec.whatwg.org/multipage/custom-elements.html) and v1.0 has been shipped in every modern browser.

In the very near future, the HTML Custom Elements specification will be incorporated into the [W3C DOM specification](https://www.w3.org/DOM/) and [WHATWG DOM Standard](https://dom.spec.whatwg.org/).

This common spec definition will inform the browser parser how to properly construct the element sans any other framework.

<a id="shadowdom"></a>
## Shadow DOM

Disambiguation: shadow DOM, shadow root, shadow tree

A set of JavaScript APIs for attaching an encapsulated "shadow" DOM tree to an element. The shadow DOM elements are rendered separately from the main document DOM and control associated functionality.

The shadow DOM is essential in keeping an element's features private, so that functionality and styles will not collide with other parts of the document.

HTML custom elements make heavy use of this is a well established specification within the [DOM Living Standard](https://dom.spec.whatwg.org/#shadow-trees).

> A shadow tree is a node tree whose root is a shadow root.

> A shadow root is always attached to another node tree through its host. A shadow tree is therefore never alone. The node tree of a shadow root’s host is sometimes referred to as the light tree.

The opportunity with the shadow DOM is [native encapsulation](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM). Standard web development is typically plagued with issues related to CSS styling and scope leaks within JavaScript.

> An important aspect of web components is encapsulation — being able to keep the markup structure, style, and behavior hidden and separate from other code on the page so that different parts do not clash, and the code can be kept nice and clean.

This native encapsulation means that developers can build custom elements to a standard that the browser will enforce thus removing the need for development maintenance.

## HTML templates

HTML templates within the scope of Web Components is a supercharged template API allowing developers to create markup templates that are not displayed to the page, but used to construct an endless number of reproductions based on a combination of logic and custom attribute properties.

<a id="itsastadndard"></a>
## It's a standard? But, no frameworks?

While building custom elements with the shadow DOM is a standard and can be authored with 100% ES6+ JavaScript, developers are encouraged to use tools that reduce complexity in code, enforce best practices and keep individual contributions D.R.Y.

Much of the research and many of the achievements made in regard to the web component spec has been done by Google Polymer Team. While the Polymer Project is transiting away from being a supporting library for building custom elements to more of an over-arching support resource, two core libraries persisted. One is [lit-html](https://lit-html.polymer-project.org/) and the other is [litElement](https://lit-element.polymer-project.org/).

### What is lit-html?

HTML templating is core to any modern development for the web. Regardless of your stack, developers are using templating in one form or another.

When building web UIs the base template structure is declarative HTML. But HTML is so low-level that there is a long history of excessively complicated and fragile solutions like server-side templating and DOM manipulation.

lit-html allows developers to express intent that mixes static and dynamic content in a declarative format that is closer to the output. lit-html simply is HTML templating in JavaScript. It's extremely small and boots fast with an easy to use API.

```js
html `
  <h1>${atricle.title}</h1>
`
```

lit-html makes heavy use of tag template literals in JavaScript to allow templates to be used within functions. As illustrated in the previous example, `html` is the function and then the content is contained within the template literal.

It should be noted that while this is similar to JSX in React, it's not the same. Specifically lit-html does not have a VDOM and does not require any special support to render HTML. This is real HTML written into a JavaScript template literal and rendered to the view.

lit-element also supports a small set of [directives](https://github.com/Polymer/lit-html/tree/master/src/directives) to customize how lit-html renders values.

lit-html is litElement's only dependency.

### What is litElement?

tl;dr

litElement is syntactic sugar on top of vanilla JS to write web components.

For the most part, the previous statement is all you really need to know about litElement. This library tool allows developers to construct a web component with little effort or regard to the boilerplate JavaScript needed to create a shadow DOM element.

litElement also provides a small set of [lifecycle hooks](https://lit-element.polymer-project.org/guide/lifecycle) for asynchronous responses to observed property changes. Full support for [event listeners](https://lit-element.polymer-project.org/guide/events), [properties](https://lit-element.polymer-project.org/guide/properties) for full web component API development as well as many other features.

<a id="aurouseslitelement"></a>
## Auro uses litElement

The really direct answer to this is, litElement and lit-html are really designed to fill a gap in development when creating web components. In today's world there are really three ways to build web components.

1. Vanilla JS
2. Web Component DSL pre-processors
3. litElement

Vanilla JS of course is where we want to be. But due to the state of browsers implementation of the v.1 spec, there is an awful lot of boilerplate code needed to build a web component.

In addition to this boilerplate code, there are legacy browsers that need to be considered and other front-end framework integration issues that need to be addressed. To this end, this is where web component pre-processors like Stencil.js and LWC from SalesForce come in.

These two pre-processors provide a custom DSL where developers can build web components to their code spec and the pre-processor will produce a common vanilla JS web component.

The use-case for Stencil is mainly with React devs that are interested in preserving their exiting code and wanting to be more flexible in application. In SalesForce's use-case, they created a very customized DSL that addresses their complex interaction needs and vast dependency on IE11 users.

Stencil.js also provides paid-for tooling that allows developers to wrap their web component code into React components that allow integration the 'React way' into their apps.

When looking at Alaska Airlines' current state of code and developer scenarios, going to something like Stencil.js seemed unnecessary as we do not have a large library of React UIs that need to carry over. The complexity of the Orion Design System at this time does not require such tooling that something like SaleForce's solution would be massive over-engineering.

Fact: building web components with vanilla JS is hard. Annoyingly hard. That brings us to lit-html and litElment. These libraries are small enough and can be individually cached with any site. Given these loaded libraries, developers at Alaska can build a vast array of web components in a style that is easier read and simpler to maintain.

<a id="resources"></a>
## Resources

Please see the following resources to learn more about Web Components, lit-html and litElement

* [litElement](https://lit-element.polymer-project.org)
* [lit-html](https://lit-html.polymer-project.org)
* [lit-HTML (Chrome Dev Summit 2017)](https://www.youtube.com/watch?v=Io6JjgckHbg)
* [lit-html by Jad Joubran](https://www.youtube.com/watch?v=LxUNvpAZf7w)
* [litElement by Jad Joubran](https://www.youtube.com/watch?v=pnH1sTPWv6I)
* [Lightning UI Platform: Web Components And Beyond](https://slideslive.com/38918861/lightning-ui-platform-web-components-and-beyond)
* [Declarative Reactive Web Components with Justin Fagnani](https://www.youtube.com/watch?v=9FB0GSOAESo)
