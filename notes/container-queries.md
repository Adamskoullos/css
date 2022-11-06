## Container Queries

1. Create container

Adding `container-type` to a class creates a css container (containment conetext), the type defines what dimension is being watched (used as the context in `@container`). For width use `inline-size`.

Add `container-name` so the container canbe grabbed for queries with `@conatiner`.

```css
.my-container {
  container-type: inline-size; /* inline-size (width) | size (width & height) | normal (none) */
  container-name: my-container;
}
```

2. Use `@container` to set media queries on the container:

```css
@container my-container (min-width: 400px) {
  /* change container layout, grab and change children styling */
}
```

### Container Units
