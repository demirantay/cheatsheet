# Tailwind CSS

Table of Contents
- [free components OSS]()
- [installation](#installation)
- [core concepts]()
- [customization]()
- [base styles]()
- [layouts]()
- [flexbox grid]()
- [spacing]()
- [sizing]()
- [typography]()
- [backgrounds]()
- [borders]()
- [effects]()
- [filters]()
- [tables]()
- [transitions animation]()
- [transforms]()
- [interactivity]()
- [svg]()
- [accessability]()

## Open Source Free Components

- ...

## Installation

__Tailwind CLI__
```sh
# ...
```

__CDN:__
```html
<head>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
```

## Core Concepts

- `Handling Hover, Focus, and Other States`

  Every utility class in Tailwind can be applied conditionally by adding a modifier to the beginning of the class name that describes the condition you want to target.

  For example, to apply the bg-sky-700 class on hover, use the hover:bg-sky-700 class:
  ```html
  <button class="bg-sky-500 hover:bg-sky-700 ...">
    Save changes
  </button>
  ```

  tailwind includes modifiers (they have everything included):
  - Pseudo-classes, like :hover, :focus, :first-child, and :required
  - Pseudo-elements, like ::before, ::after, ::placeholder, and ::selection
  - Media and feature queries, like responsive breakpoints, dark mode, and prefers-reduced-motion
  - Attribute selectors, like [dir="rtl"] and [open]

  [view fully on the documentation](https://tailwindcss.com/docs/hover-focus-and-other-states)

- `Responsive Design`
  There are five breakpoints by default, inspired by common device resolutions:
  - 1 - `sm` ->	640px -> @media (min-width: 640px) { ... }
  - 2 -
  - 3 -
  - 4 -
  - 5 -

- `Dark Mode`

- `Reusing Styles`

- `Custom Styles`

- `Functions and Derivatives`

## Customization


