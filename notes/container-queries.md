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

When using `inline-size` we have access to container width units:

- **cqw** > 50cqw = 50% width of container
- **cqi** > `i` stands for inline-size and is dynamic depending on the container width. This is nice for dynamic font size depending on contaner width.
  The below example dynamically sets the font size to `10cqi`....dependant on the container. `clamp` is also used to set min and max sizes:

Child element:

```css
.title {
  font-size: clamp(2.5rem, 10cqi, 5 rem); /* clamp: min, target, max */
}
```
