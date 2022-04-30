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

![Screenshot from 2022-04-30 10-30-12](https://user-images.githubusercontent.com/73107656/166100131-7cdadf80-071e-4d01-ab1e-7a6c6811103f.png)

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

`flex: 0 1 150px;`:
![Screenshot from 2022-04-30 10-32-48](https://user-images.githubusercontent.com/73107656/166100184-763a857d-4125-44e4-8b56-ad81a80b6018.png)

`flex: 1 1 150px;`:
![Screenshot from 2022-04-30 10-33-39](https://user-images.githubusercontent.com/73107656/166100210-f010ca0f-0aad-465d-90a0-3959f3326960.png)

---

## Grid with Side Bar

The blow example creates a `2 column grid` where the left column has a min width of 150px and a max width of 25%, then the right column has been given `1fr` meaning it will take up the remaining width of the view or container

```css
.parent {
  display: grid;
  grid-template-columns: minmax(150px, 25%) 1fr;
}
```

![Screenshot from 2022-04-30 10-35-00](https://user-images.githubusercontent.com/73107656/166100270-e980c4f6-e842-47ea-95cc-3ad0de84aa33.png)

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

![Screenshot from 2022-04-30 10-35-44](https://user-images.githubusercontent.com/73107656/166100292-9950fe81-692d-42e2-8748-b8d2b1f425a7.png)

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

![Screenshot from 2022-04-30 10-36-26](https://user-images.githubusercontent.com/73107656/166100307-25077f8c-bfb4-4a98-9fc4-a8129400f203.png)

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

![Screenshot from 2022-04-30 10-37-12](https://user-images.githubusercontent.com/73107656/166100320-a376acd3-6255-4357-81b0-1c6e1a1f1dc7.png)

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
![Screenshot from 2022-04-30 10-39-26](https://user-images.githubusercontent.com/73107656/166100393-bc0c0a5f-5e91-4e1b-a7e8-a2824ea01401.png)

**auto-fill**:
![Screenshot from 2022-04-30 10-38-13](https://user-images.githubusercontent.com/73107656/166100348-06fd8c1b-b09f-40ff-9d6f-8425b7a6f726.png)

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

![Screenshot from 2022-04-30 10-40-53](https://user-images.githubusercontent.com/73107656/166100430-05b4ecaf-9767-4fd2-84c1-3505600a494a.png)

---

## Using clamp to dynamically manage width

width: clamp(`min`, `actual`, `max`);

```css
.card {
  width: clamp(100px, 30%, 150px);
}
```

![Screenshot from 2022-04-30 10-41-40](https://user-images.githubusercontent.com/73107656/166100451-b41ce7a2-f76c-4b6a-b466-bb49bebd1124.png)
**Note**: Can use `clamp` with `font-size`

---

## Maintaining an images Aspect Ratio

```css
.image-container {
  aspect-ratio: 16 / 9;
}
```

![Screenshot from 2022-04-30 10-42-33](https://user-images.githubusercontent.com/73107656/166100487-d7727de9-b63f-48cb-a47d-6bcf518f45d0.png)
