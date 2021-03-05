# CSS Development Conventions

The implementation of Auro CSS uses a naming convention model that will be strictly adhered to throughout this library and compliance is expected for any contributed updates.

## Single Responsibility

Selectors are to follow a rule of **Single Responsibility**, this is to ensure that CSS selectors are not managing overlapping UI responsibilities. This is not to be confused with **functional css** or **OOCSS** writing styles. The goal of single responsibility in this context is to ensure that the focus of the selector is maintaining scope of the task it is performing. Any code that uses selector tree dependency/specificity techniques will be considered non-complaint.

A term I like to use is a **Pure Selector**. Pure Selectors should **NEVER** have a dependency on a parent selector, nor should it have any side-effects when used as a descendant selector. Much in the same way pure functions exist in other languages, the desire is the same*.

1. When used, the output/result should always be the same
1. Produces no side-effects

*Exception to this rule is in conjunction with the `:host()` selector.

### Meets compliance standards

```scss
.FormGroup {
  padding: var(--auro-size-md);
  margin-bottom: var(--auro-size-sm);
}

.inputElement {
  font-size: var(--auro-text-body-size-default);
  border: 1px solid var(--auro-color-ui-default-on-light);
  padding: var(--auro-size-md);
}

.inputElement--xxl {
  font-size: var(--auro-text-heading-display-size-breakpoint-lg);
  padding: var(--auro-size-lg);
}

.FormGroup-inputElement {
  margin-bottom: var(--auro-size-sm);
}
```

### Fails compliance standards

```scss
.FormGroup {
  padding: var(--auro-size-md);
  margin-bottom: var(--auro-size-sm);

  .inputElement {
    margin-bottom: var(--auro-size-sm);
  }
}

.inputElement {
  font-size: var(--auro-text-body-size-default);
  border: 1px solid var(--auro-color-ui-default-on-light);
  padding: var(--auro-size-md);

  &.large {
    font-size: var(--auro-text-heading-display-size-breakpoint-lg);
    padding: var(--auro-size-lg);
  }
}
```

In context of the Orion Design System there are a few basic concepts; tokens, utilities, elements, components, objects, experiences and finally state. These concepts are defined below with examples.

## Token

Shared resources for foundational CSS values
(describes CSS values)

```
{
  "color": {
    "base": {
      "white": {
        "value": "ffffff",
        "comment": "{comments.color.base.value.comment}"
      }
    }
  }
}
```

## Utility

Universally applicable solution in cases where applying this style is not an appropriate responsibility of another selector. These selectors are typically considered UI trump cards as they may use the `!important` flag. These are last resort DOM utility classes and have cascading effects to be aware of.

(may define shape or layout without direct context to any element, component or object)

```scss
.util_hidden {
  display: none !important;
}

.util_hiddenVisually {
  border: 0 !important;
  clip: rect(1px, 1px, 1px, 1px) !important;
  height: 1px !important;
  overflow: hidden !important;
  padding: 0 !important;
  position: absolute !important;
  width: 1px !important;
}
```

Naming convention: use camel casing prefixed with the `util_` string

## Primitive Component / Element

Any part of a designed/functional (thing - common noun) that cannot independently complete a task

(is responsible for the shape of any UI element, does not effect layout outside it’s immediate context)

```scss
.inputElement {
  border: 1px solid var(--auro-color-ui-default-on-light);
  padding: var(--auro-size-lg);
}
```

Naming convention: use camel casing

## Component in global context

A (thing - common noun) made up of Primitive Components that can complete a task

(is responsible for the shape of the component, does not effect layout outside it’s immediate context)

```scss
.FormGroup {
  padding: var(--auro-size-lg);
}
```

## Component in encapsulated custom element context

A (thing - common noun) that can either be a primitive or made up of other Primitive Components that can complete a task

(is responsible for the shape of the component, does not effect layout outside it’s immediate context)

> The `:host()` CSS pseudo-class function selects the shadow host of the shadow DOM containing the CSS it is used inside (so you can select a custom element from inside its shadow DOM) — but only if the selector given as the function's parameter matches the shadow host.

--source [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/:host())

```scss
:host() {
  padding: var(--auro-size-lg);
}
```

This selector is also allowed to break the compliance disallowing child selectors. The `:host` selector is special that is can be used to determine an alternate output of a selector within the scope of the custom element based in a change of the parent. Something that standard global CSS cannot do.

In this example, the attribute of `thin` placed in the custom element DOM would trigger this style change.

```scss
:host([thin]) {
  .FormGroup-inputElement {
    margin-bottom: 0;
  }
}

## Component Element

An Element's shape within the context of a Component

(responsible only for the management of an element's shape within the context of a Component, does not effect layout outside it’s immediate context nor the shape of the base element)

```scss
.FormGroup-inputElement {
  margin: 0 var(--auro-size-md)
}
```

Naming convention: use respective conventions with single hyphen `-` between Component and Element

## Modifiers

An [alternate descriptor - adjective] that alters the appearance of an element, component or object.

Bind modifiers directly to the primitive, component or object. DO NOT use modifiers with combination selectors.

#### DO

```scss
.inputElement--xxl { ... }

.FormGroup--xxl { ... }

.obj_Header--xxl { ... }
```

#### DO NOT

```scss
.FormGroup-inputElement--xxl { ... }

.exp_Homepage-obj_FlightSummary--xxl { ... }
```

Naming convention: use a double-dash `--` between the selector name and the modifier suffix

## State

An [alternate descriptor - verb] that alters the state appearance of an element, component or object.

Defining non-standard appearances of state uses a special set of utility adjoining selectors.

```scss
.elementThing.isExpanded { ... }
```

Defining standard appearances of state uses standard pseudo-classes

```scss
.elementThing:disabled { ... }
```

Using utility adjoining selectors for HTML defined standard appearances will be considered non-compliant to standard.

* Pseudo-classes apply globally
  * ` hidden`
  * `draggable`
  * `:active`
* Pseudo-classes apply to the `<a>` element
  * `:hover`
  * `:visited`
  * `:hover`
* Pseudo-classe apply to the `<input>` element
  * `checked`
* Pseudo-classe apply to the `<button>, <fieldset>, <input>, <optgroup>, <option>, <select>, <textarea>` elements
  * `disabled`
