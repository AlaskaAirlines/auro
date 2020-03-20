# Welcome to LitElement and Lit-HTML

Here students will learn about how to develop HTML custom elements using the supporting libraries of Lit-Element and Lit-HTML.

### Intro to Polymer and Lit-Element/Lit-HTML

First, there was Polymer, and then there is Lit-Element. This lesson will focus on the history of Google's Polymer project, where it came from and where it is going.

NOTE: This lesson will be a [detailed history](https://www.polymer-project.org/blog/) of the Polymer project and how it evolved into Lit-element and Lit-HTML. Take the students on a journey from the 1.0 release up to its current version as managed by Justin Fagnani.

### Standard HTML/CSS/JS, let's build our 1st component

In this lesson, students will learn the basic construct for building an HTML custom element with Lit-Element with nothing more than HTML/CSS/JS. This lesson will also cover new concepts introduced with the ES6 syntax.

NOTE: setup example using browser-sync for side-by-side code and view

NOTE: This lesson starts the hands-on learning portion of the course. Students will be walked through the creation of a new custom element within the scope of a simple HTML example.

Note: for example, thinking a table component would be the best example

1. import the polyfill
1. script type="module"
1. create the es6 class extending LitElement
1. HTML Templates and tagged template literals

### Using properties and building the API

In this lesson, students will learn about property options, how to declare properties, how to initialize property values in the element constructor and from attributes in markup, configure attributes and property accessors.

NOTE: build an example where all different types of properties are used, even an object that a loop can iterate over for a result in the view.

### The HTML \<slot>

In this lesson, students will learn how to use the \<slot> element and slot defaults within the scope of another component. This lesson will also include tips and tricks for using named slots to control content options within a component.

### Nesting child components

In this lesson, students will learn how to not only nest a component inside a component but also use the \<slot> element as well to nest components.

NOTE: be sure to mention that even with nested components the shadow DOM is doing the same thing. CSS and other things like aria-roles DO NOT transfer between components through the shadow DOM.

### The basics of event handling

In this lesson, students will learn about how to use lit-HTML `@event` bindings inside a template within the render function to add event listeners to the component.

NOTE: Address topics as [listed in the API](https://lit-element.polymer-project.org/guide/events#working-with-events-and-shadow-dom)

NOTE: The default JavaScript context object `this` inside an event handler belonging to a LitElement-based component is the component itself.

NOTE: illustrate a pattern where a method can be bound to the `this` object in the constructor as not have to reference `this` in the `render()` method.

### Advanced templating

In this lesson, students will learn about the advanced templating techniques you can do within the HTML named template literal such as the different binding types, if statements and loops. Also, this lesson will include examples for using some of the more helpful built-in directives.

### The basics of event listeners

In this lesson, students will learn how to bind listening events to elements within the shadow DOM

### Render lifecycle methods

In this lesson, students will learn the basics of lifecycle methods to effect change within a component based on different property types.

NOTE: working with numbers or strings, updates are simple to update and do not need additional support. But working with objects/arrays, additional tools like `this.requestUpdate()` are needed.


# Styling web components

In this category, students will come to be more comfortable with the concepts of CSS and the shadow DOM.

### What is the shadow DOM

In this lesson, students will come to understand what the shadow DOM versus the light DOM and why this is extremely useful concerning building custom elements.

NOTE: Not to be confused with the virtual DOM. In short, what happens in the shadow DOM, stays in the shadow DOM. This will also be a good time to make note that not all components have to be in the shadow DOM.

NOTE: Take this opportunity to illustrate how CSS outside the scope of a custom element does not affect elements inside the shadow DOM and vice-versa.

NOTE: This lesson should illustrate what will and will not pierce the shadow DOM.

### CSS Custom Properties

In this lesson, students will learn the basics of CSS custom properties (aka CSS variables) and how they play an essential role in custom elements.

### Styling and theming with the :host {} selector

In this lesson students will learn the difference between the `:root{}` and the `:host{}` selector when it comes to defining CSS custom properties and applying styles to the host custom element that encompasses the HTML template.

### The static styles property and scoped styles in the template

In this lesson, students will learn the difference between using the static styles property and defining the styles in the HTML template.

In this lesson students will learn the most basic way to inject styles into the scope of a custom element using the `styles()` method. This lesson will also include advanced options like evaluating properties to change the CSS of an element.

### Using expressions with properties and other theming techniques

This lesson will provide examples of how to use element properties to pass in options that will alter the output UI of the element. This will include simple options like directly passing in a value and more advanced use cases like using lit-HTML's classMap directive for applying decisions from a property to affect the style.

NOTE: look at the new ods-inputoptions for a really good example of using classMap

### Using Sass with web components

In this lesson, students will learn how to apply advanced CSS techniques using Sass and how to inject these stylesheets into the scope of a custom element.

### Other advanced techniques

In this lesson, students will learn about techniques like using the `::part()` selector for applying custom styles within the scope of an element as well as using CSS custom properties. Students will also be introduced to new advanced techniques using the static styles method with the CSS named template literal for using CSS in JS.




# Open-WC 101

In this category, students will be introduced to advanced support examples regarding the Open-WC framework and its toolset.

### What is Open-WC?

In this lesson, students will be introduced to the Open-WC library of tooling.

### Open-WCs automated testing tooling

In this lesson, students will be introduced in more depth to the automated test tooling that comes with Open-WC and be walked through a series of instructions as to how to best test and maintain sanity over custom elements.
