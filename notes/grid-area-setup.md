## Grid Area Setup

### Create grid for mobile

```css
.grid {
  display: grid;
  gap: 10px;
  grid-auto-columns: 1fr; /* Ensure each auto generated column is the same */
  grid-template-areas:
    "one"
    "two"
    "three"
    "four";
}
```

### Assign grid areas to elements

```css
.grid-item:nth-child(1) {
  grid-area: one;
}
```

### Alter grid layout at breakpoints

```css
@media (min-max: 678px) {
  .grid {
    grid-template-areas:
      "one one"
      "two three"
      "four four";
  }
}
```

```css
@media (min-max: 900px) {
  .grid {
    grid-template-areas:
      "one one two"
      "three four four";
  }
}
```
