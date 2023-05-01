## Bulma Cheatsheet

### Installation

Bulma is a CSS file, you can include it with just basic css and html from a CDN source:
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css">
```
In order for bulma to work correctly you need these two (responsivness):
```html
<!DOCTYPE html>
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Modifiers

In Bulma you have a generic container class and a `is-*` modifier to that class. For example you can have a basic bulma button with:
```html
<button class="button">
  Button
</button>
```
And now you can add a customization with :
```html
<button class="button is-primary">
  Button
</button>
```

## Columns

### Basics


Building a columns layout with Bulma is very simple:
- 1 - Add a columns container
- 2 - Add as many column elements as you want

Each column will have an equal width, no matter the number of columns.

```html
<div class="columns">
  <div class="column">
    First column
  </div>
  <div class="column">
    Second column
  </div>
  <div class="column">
    Third column
  </div>
  <div class="column">
    Fourth column
  </div>
</div>

```

### Sizes

If you want to change the size of a single column, you can use one of the following classes:
- `is-three-quarters`
- `is-two-thirds`
- `is-half`
- `is-one-third`
- `is-one-quarter`
- `is-full`

```html
<div class="columns">
  <div class="column is-four-fifths">is-four-fifths</div>
  <div class="column">Auto</div>
  <div class="column">Auto</div>
</div>
```

or you can use 12 grid system:
- `is-1`
- `is-2`
- `is-3`
- `is-4`
- `is-5`
- `is-6`
- `is-7`
- `is-8`
- `is-9`
- `is-10`
- `is-11`
- `is-12`

### Gap

If you want to remove the space between the columns, add the is-gapless modifier on the columns container:
```html
div class="columns is-gapless">
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
  <div class="column">
    No gap
  </div>
</div>
```

You can specify a custom column gap by appending one of 9 modifiers on the .columns container.
- `is-0` will remove any gap (similar to is-gapless)
- `is-3` is the default value, equivalent to the 0.75rem value
- `is-8` is the maximum gap of 2rem

### Options