# 14. Grid

## Content

- what is grid
- columns and rows
- grid properties and values
- repeat, min, max functions
- template areas
- grid vs flexbox

## CSS Grid

- a layout that is popular for arranging the components on a webpage
- stuff like bootstrap, bulma, figma, etc uses grid for making layouts

sidenote: Firefox has better debugging tools for grid than Chrome

## grid-items

Remember, the grid-items should not have their width or height hard coded.

They inherit those values from the columns and rows they inhabit.

Therefore, if a grid-item's column is 200px and its row is 400px, the grid-item's width is 200px and its height is 400px

## minmax()

This should be easy.

`grid-template-rows: 1fr minmax(10px, 200px) 2fr;`

Here we have 3 rows:

- the second one where we use the minmax() function means we want that row never to go below 10px or over 200px
- it works just like min-width || max-width etc
- it is used to ensure certain thresholds aren't crossed when the viewport width becomes to narrow or too wide

## grid-column/row-start/end

You can use these four properties within a grid item to determine where it should go on the grid.

As you can already tell, `start` carries the number of the row/column you wish the item to start on and vice versa for end

Later we will learn about a fancier way to do this with template areas.

## named lines

This is an alternative to the above using names rather than grid row/column numbers

```html
<div class="container">
  <div class="grid-item a">Item 1</div>
  <div class="grid-item b">Item 2</div>
  <div class="grid-item c">Item 3</div>
  <div class="grid-item">Item 4</div>
  <div class="grid-item">Item 5</div>
  <div class="grid-item">Item 6</div>
</div>
```

```css
.container {
  background-color: rgb(187, 150, 223);
  border: 3px solid whitesmoke;
  display: grid;
  grid-template-columns: [start-line] 200px [middle-line] 200px [end-line] 300px [very-end];
}

.grid-item {
  background-color: cornsilk;
  height: 6rem;
  border: solid 1px lightcoral;
}

.a {
  grid-column-start: start-line;
  grid-column-end: very-end;
}
```

As you can see, we can control the position of `grid-item a` using the names we created in `grid-template-columns`

See the directory `named-lines` to see it in action

## grid-column/row shorthand

instead of using

```css
.a {
  grid-column-start: start-line;
  grid-column-end: very-end;
}
```

You use the shorthand

```css
.a {
  grid-column: start-line / very-end;
}
```

Works the same way for `grid-row`

Remember, these go inside of the flex items

### grid-area

This is an even shorter shorthand of grid-column/row

It combines both in one

```css
.a {
  grid-area: row-1 / column-1 / row-3 / column-2;
}
```

This uses 4 values: the row you want to start one / the column you want to start on / the row you want to end on / the column you want to end on

Naturally, you can use the column/row number or the name if you gave them one

## grid-gap

this is the grid version of the `gap` property in flex containers.

this goes inside of the grid container and allows you to set a gap between the items

remember to use the same value for rows and columns for best design practice

`.grid-container { grid-gap: 2rem; }`

## named template areas

`grid-template-areas` goes inside of the flex container

`grid-area` goes inside of the flex item

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(6, 1fr);
  grid-template-areas:
    "header header header header"
    "aside main main main"
    "aside main main main"
    "aside main main main"
    "aside main main main"
    "footer footer footer footer";
}

.grid-item-1 {
  grid-area: header;
}

.grid-item-2 {
  grid-area: aside;
}

.grid-item-3 {
  grid-area: main;
}

.grid-item-4 {
  grid-area: footer;
}
```

this is the best way to make outlines or layouts of your web page.

## Grid on this Project

We will use grid to sustain our layout. Although this has already been achieved, we will look at how we can make it w/ grid.

As for the modal, mobile nav menu, overlay, these will not be accounted for grid items because their display property is not `static` so they ignored even if their parent container is using grid.

Use named template areas to fit the header, main, footer

## fit-content()

```css
.grid-container {
  grid-template-columns: 1fr 2fr fit-content(8rem);
}
```

This function makes sure that the column/row does not exceed whatever value you pass into it by squeezing the content into the provided value.
