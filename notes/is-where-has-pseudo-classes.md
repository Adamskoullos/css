## is | where | has Pseudo Classes

### is

```css
header :is(h1, h2) {
  ...;
}

header :is(.title) {
  ...;
}

.container:is(.main-content, .side-bar) {
  ...;
}

:is(header, main) h2 {
  ...;
}
```

### is vs where

`is` and `where` are used in the same way however the `specificity` is treated differently.

The highest rank item within `is` is included in the spcificity and in `where` the items are not included:

```css
:is(header, main) h2 {
  ...;
} /* 0.0.0.2 */

:where(header, main) h2 {
  ...;
} /* 0.0.0.1 */
```

### has

```css
p:has(span) {
  /* applies to parent that has a span child */
}

p:has(> img) {
  /* style parent if it has a direct child img */
}

p:has(+ p) {
  /* If parent has a sibling after it apply these styles */
}

p:not(:has(span)) {
  /* if parent does not have a span inside, apply these styles */
}

form:has(:invalid) {
  /* if condition exists within form, style the form */
} /* conditions are given the same specificity as a class */
```
