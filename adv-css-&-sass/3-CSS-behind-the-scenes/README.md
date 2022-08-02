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

## How CSS is Parsed

### Cascade and Specificity

Some Terminology:

- CSS Rule = selector + declaration block (everything that goes inside the curly braces)
- declaration = property + value in the curly braces

When a CSS file is being parsed by the browser, the browser's first job is to resolve any conflict of styles affecting the same element.

- specificity is what decides which selector wins
- also, selectors at the bottom of the CSS file take priority
- CSS files that are linked last on the HTML file also take priority

Last two bullet points should give you the idea behind `cascade` style sheets

### Value Processing

After the browser figures out which elements get X styles, it needs to figure what all the units are in pixels.

Naturally, `90vw` in pixels is different if you are talking about a desktop monitor and a smartphone's.

This is what the browserd does: it converts any units that were declared w/o pixels into pixels in relation to the device upon which it is being rendered.

### Inheritance

### CSSOM
