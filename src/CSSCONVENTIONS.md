# CSS Development Conventions

The implementation of Orion Web Code Style Sheets uses a naming convention model that will be strictly adhered to throughout this library and compliance is expected for any contributed updates.

## Single Responsibility

Selectors are to follow a rule of **Single Responsibility**, this is to ensure that CSS selectors are not managing overlapping UI responsibilities. This is not to be confused with **functional css** or **OOCSS** writing styles. The goal of single responsibility in this context is to ensure that the focus of the selector is maintaining scope of the task it is performing. Any code that uses selector tree dependency/specificity techniques will be considered non-complaint.

A term I like to use is a **Pure Selector**. Pure Selectors should **NEVER** have a dependency on a parent selector, nor should it have any side-effects when used as a descendant selector. Much in the same way pure functions exist in other languages, the desire is the same.

1. When used, the output/result should always be the same
1. Produces no side-effects

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

Any part of a designed/functional [thing - common noun] that cannot independently complete a task

(is responsible for the shape of any UI element, does not effect layout outside it’s immediate context)

```scss
.inputElement {
  border: 1px solid var(--auro-color-ui-default-on-light);
  padding: var(--auro-size-lg);
}
```

Naming convention: use camel casing

## Component

A [thing - common noun] made up of Primitive Components that can complete a task

(is responsible for the shape of the component, does not effect layout outside it’s immediate context)

```scss
.FormGroup {
  padding: var(--auro-size-lg);
}
```

Naming convention: use pascal casing

## Component Element

An Element's shape within the context of a Component

(responsible only for the management of an element's shape within the context of a Component, does not effect layout outside it’s immediate context nor the shape of the base element)

```scss
.FormGroup-inputElement {
  margin: 0 var(--auro-size-md)
}
```

Naming convention: use respective conventions with single hyphen `-` between Component and Element

## Object

A [thing - common noun] made up of Components, is functionality self-contained, and maintains usability on its own in any context

(is responsible for the shape of the object, does not effect layout outside it’s immediate context)

```scss
.obj_FlightSummary { ... }

.obj_Header { ... }

.obj_Footer { ... }
```

Naming convention: use pascal casing prefixed with the `obj_` string

## Object component(s)

A Component's shape within the context of a Object

```scss
.obj_FlightSummary-FormGroup { ... }
```

Naming convention: use pascal casing prefixed with the `obj_` string and single hyphen `-` between Object and Component

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
