# 3. CSS Behind the Scenes

## Three Pillars of Writing Good HTML & CSS

1. Responsive Design

   - fluid webpage layouts
   - media queries
   - responsive images
   - correct units
   - mobile first

2. Maintainable & Scalable Code

   - clean
   - easy to read
   - growth
   - reusable
   - organized files
   - class names (BEM)
   - organized HTML structure

3. Performance
   - less HTTP requests
   - less code
   - compress code
   - CSS preprocessor (SASS)
   - less images
   - compressed images

## How Browsers Read our Files

1. Browsers read the HTML as they download it
2. They then create a virtual representation of the HTML via DOM
3. As it does this, it reads the CSS file linked in the head element
4. the browser figures out which selector takes priority in any overlap
5. it also converts units into pixels, e.g. rem/%/vh/ into pixels
6. CSS is virutally rendered into a CSSOM (CSS Object Model)
7. Both the DOM and CSSOM are combined into a `render tree` and finally displayed on the browser
