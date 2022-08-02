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

This is what the browser does: it converts any units that were declared w/o pixels into pixels in relation to the device upon which it is being rendered.

### Inheritance

If a child element does not a specific declaration, it will inherit that from its parent.

It will also inherit computed values from its parent.

```css
.parent {
  font-size: 20px;
  line-height: 150%;
}

.child {
  font-size: 25px;
}
```

The child will inherit a `line-height` of 30px (20 _1.5) and not 37.5px (25 _ 1.5). This is because it has inherited the **computed value** from its parent.

Anyway, inheritance is a key component to writing maintainable code that is not bloated.

#### Inheritance in Action

We are going to convert all the units in our CSS file into REM. Why? because all we have to do is increase or decrease the global font-size in `html { }` in media queries instead of making a bunch of selectors for h1, h2, h3, etc.

```css
html {
  font-size: 10px; /* 62.5% */
}
```

Now REM is going to be easy to work with. 1 REM = 10 pixels.

Replace all the pixel units in Natour with rem

- 5px -> .5rem
- it is standard practice in CSS to leave out the zero in decimals
- .5rem is good
- 0.5rem is bad

Now our life has been made so much easier.

- if a user has changed their default font-size in the browser, our page is responsive (we must use the percentage unit not pizels to get this to work, i.e. 62.5% not 10px)
- if we need make things bigger for desktop, we just change `html { font-size: 62.5%; }` to `70%` and with one line we saved our selves so much work

### CSSOM
