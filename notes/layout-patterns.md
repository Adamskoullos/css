## Powerful Layout Patterns

- [Center Items Grid](#Center-Items-Grid)
- [Flex Grow/Shrink/Basis](#Flex-Grow/Shrink/Basis)
- [Grid with Side Bar](#Grid-with-Side-Bar)
- [Grid Header/Content/Footer Setup](#Grid-Header/Content/Footer-Setup)
- [Grid Holy Grail Layout](#Grid-Holy-Grail-Layout)
- [Flex Manage Card Elements](#Flex-Manage-Card-Elements)
- [Using clamp to dynamically manage width](#Using-clamp-to-dynamically-manage-width)
- [Maintaining an images Aspect Ratio](#Maintaining-an-images-Aspect-Ratio)

---

### Center Items Grid

```css
.parent {
  display: grid;
  place-items: center;
}
```

---

### Flex Grow/Shrink/Basis

flex: `grow` `shrink` `baseWidth`;

```css
.parent {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.children {
  flex: 1 1 150px; /* Stretching */
  flex: 0 1 150px; /* No stretching */
  margin: 5px;
}
```

---

## Grid with Side Bar

The blow example creates a `2 column grid` where the left column has a min width of 150px and a max width of 25%, then the right column has been given `1fr` meaning it will take up the remaining width of the view or container

```css
.parent {
  display: grid;
  grid-template-columns: minmax(150px, 25%) 1fr;
}
```

---

## Grid Header/Content/Footer Setup

grid-template-rows: `header` `content` `footer`;

`auto` allwos the row to take up as much space as the internal content requires so this is used for both the header and footer. Then `1fr` is used for the content which takes up the remaining space of the view pushing the header and footer apart.

```css
.parent {
  display: grid;
  grid-template-rows: auto 1fr auto;
}
```

---

## Grid Holy Grail Layout

This layout includes header footer with aside sections either side of the main content.

grid-template: `headerRow` `contentRow` `footerRow` / `leftColumn` `mainContent` `rightColumn`;

```css
.parent {
  display: grid;
  grid-template: auto 1fr auto / auto 1fr auto;
}
.header {
  padding: 2rem;
  grid-column: 1/4;
}
.footer {
  padding: 2rem;
  grid-column: 1/4;
}
.left-side {
  grid-column: 1/2;
}
.right-side {
  grid-column: 3/4;
}
```

---

## 12 Column Grid

We can easily create a a 12 column grid:

```css
.parent {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
}
```

An and place child elements wherever we need them to be:

```css
.child {
  grid-column: 1/4;
}
```

---

## RAM Repeat Auto Minmax

```css
.parent {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  /* auto-fill > maintains each child's width to the baseWidth (150px) on larger screens*/
  /* auto-fit > allows each child to fill the remaining space con larger screens*/
}
```

**auto-fit**:

**auto-fill**:

---

## Flex Manage Card Elements

When we want the elements in each card to take up the full height of card and be consistently structured regardless of the content in each card we can use the following pattern:

```css
.card {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  justify-content: space-between;
}
```

---

## Using clamp to dynamically manage width

width: clamp(`min`, `actual`, `max`);

```css
.card {
  width: clamp(100px, 30%, 150px);
}
```

**Note**: Can use `clamp` with `font-size`

---

## Maintaining an images Aspect Ratio

```css
.image-container {
  aspect-ratio: 16 / 9;
}
```
