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
