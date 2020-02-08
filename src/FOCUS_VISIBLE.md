# Accessibility focus visible

![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/ods-docs.svg?color=orange)

One of the core pillars for supporting accessibility (a11y) within a modern web application is through maintaining the state of focus as a user tabs through an interface. The current implementation of this a11y state is via the `:focus` state introduced in CSS Level 2 (Revision 1).

For a11y reasons, according to the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus#Accessibility_Concerns), it is advised to NEVER remove the browsers default settings without replacing it with a sufficient substitute.

```css
:focus { outline: none; }
```

> Never just remove the focus outline (visible focus indicator) without replacing it with a focus outline that will pass [WCAG 2.1 SC 1.4.11 Non-Text Contrast](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html)

## Design concerns

In contrast to the a11y issue, there is typically a design concern with the `:focus` state as an element within a web app has focus regardless of tab, click or tap. As a result of that, unless there is a requirement to maintain a11y the `:focus` state is typically disabled.

For projects that have an a11y requirement, this is not an option. This in itself is a large design challenge and one with many opportunities.

## Selectors Level 4 specification

In the next selector level specification draft is [9.4. The Focus-Indicated Pseudo-class: :focus-visible](https://drafts.csswg.org/selectors-4/#the-focus-visible-pseudo).

> The :focus-visible pseudo-class applies while an element matches the :focus pseudo-class and the user agent determines via heuristics that the focus should be made evident on the element.

The purpose of this new CSS spec is to allow for developers to build interfaces that speaks specifically to their special needs audience while not having to adjust the experience for those who do not require additional interaction feedback. This also allows for designers to design very specific interactions for those who require additional interaction feedback.

### Focus visible polyfill

This [polyfill](https://www.npmjs.com/package/focus-visible). based on the proposed CSS pseudo selector, allows for this functionality today.

> Based on the proposed CSS :focus-visible pseudo-selector, this prototype adds a focus-visible class to the focused element, in situations in which the :focus-visible pseudo-selector should match.

The polyfill has been tested in a number of situations and has great support from the community and its users.

### How to use

The [focus visible](https://www.npmjs.com/package/focus-visible) npm package is a peer dependency with all Orion UI and its components. Ensuring that focus-visible is loaded with your project's javascript is the only primary dependency.

Within any web core or custom element CSS, the use of this feature requires use of the `.focus-visible` selector, NOT `:focus`. In fact, within [Orion](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets/blob/master/src/_baselineLTE.scss) the default `:focus` state is removed from all browsers allowing for the `.focus-visible` selector manage the interaction.

### Focus visible and custom elements

It is important to remember that the focus-visible tab feature will NOT tab into the shadow DOM of a custom element. When tabbing through an interface, the `focus-visible` selector will be placed on the host element of a custom element. The CSS within the custom element will need to be aware of the outer host use of the `focus-visible` selector update. The following example is how to write a CSS selector that will be inside the shadow DOM, but aware of updates to the host custom element.

```css
:host(.focus-visible) {
  .button {
    ...
  }
}
```

##
<footer>
Alaska Airlines Auro Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
