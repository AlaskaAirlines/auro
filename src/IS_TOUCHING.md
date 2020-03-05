# CSS hover and is-touching support

Within all UIs is the option to hover over an element and have an interactive response. When it comes to mobile-first design and development, the hover scenario is largely ignored as it is impossible to track a hover with a touch device.

It also should be noted that a hover event should not be supported in mobile-first development as the hover will be apparent with the fist tap, then the active or focus state will be visualized.

## Auro and hover support 

In the Auro Design System, the concept of a hover is supported, but it is important to keep this interaction away from touch users. 

### w/CSS

This can easily be address via CSS by using the `@media (hover: hover)` [feature](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/hover) as illustrated in the example blow. 

```scss
@media (hover: hover) {
  &:active, 
  &:hover {
    background-color: var(--auro-color-ui-hover-on-light);
    border: 1px solid var(--auro-color-ui-hover-on-light);
  }
}
```

Using this example, the `hover` and `active` states will only fire in the browser if the device supports hover events. Mainly, this will not fire on touch devices. 


### w/JavaScript and CSS

Within each component a function could listen for a [touchstart](https://developer.mozilla.org/en-US/docs/Web/API/Element/touchstart_event) event that is part of the larger [touch events](https://developer.mozilla.org/en-US/docs/Web/API/Touch_events) specification.

> In order to provide quality support for touch-based user interfaces, touch events offer the ability to interpret finger (or stylus) activity on touch screens or trackpads.

```javascript
this.addEventListener('touchstart', function() {
  this.classList.add('is-touching');
});
```

The purpose of this function is to place a `.is-touching` selector on any element as a user interacts with it. The goal being that if a user 'touches' the device, the element will have the `.is-touching` selector placed in the DOM and the CSS should be written so that a `:hover` event will not be added to that element.

#### CSS support for JavaScript solution

It is important to remember that the touch event will be associated to the host custom element and not any part of the inner shadow DOM HTML.

As illustrated in this example, when the selector `:host` does NOT have the `.is-touching` selector applied to the host custom element, then the `:hover` selector will be applied. Whereas if the `.is-touching` selector IS on the host custom element, the `:hover` will not be applied.

```scss
:host(:not(.is-touching)) & {
  &:active, 
  &:hover {
    background-color: var(--auro-color-ui-hover-on-light);
    border: 1px solid var(--auro-color-ui-hover-on-light);
  }
}
```
