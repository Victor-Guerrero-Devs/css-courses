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

This virtualization of the styles takes these into account

- box model
- box types (block, inline, inline-block)
- position (relative, absolute, fixed) of elements
- stacking context (z-index)

Once it has put the values of all these things through an algorithm, it can now apply those styles on the DOM it has created and render the page on your browser.

## CSS Architecture

The pieces that determine if your CSS Architecture is any good are:

- clean?
- good naming convention?
- modular?
- easy to add to?
- reusable?
- great directory?

You should plan out your projects like this:

- make a barebones wire frame of your webpage layout
- make a high fidelity replica of it in figma
- construct the HTML skeleton
- start building the CSS on the largest components first and work yourself down to the smallest

You should:

- use component driven design (create the building blocks first like in `Moshify`)
  - build blocks that stand on their own
  - come together to build components via layout
  - re-usable across the project and any other project
  - blocks must be independent from one another

As for the directory for CSS, there is a popular one called `the 7-1 pattern`

You have 7 different folders which handle

- base/
- components/
  - one file per component
- layout/
  - one file per layout (desktop, tablet, mobile)
- pages/
  - specific styles for pages
- themes/
  - different themes if any
- abstracts/
  - variables etc
- vendors/
  - 3rd party CSS

Each folder has small CSS files that are obviously related the to folder name and all of these small CSS files are imported into a main one.

Finally, more than often, they are written in SASS (or any other CSS pre-processor) and converted to CSS during production.

## Using BEM in Natour

```html
<header class="header">
  <div class="header__logo-box">
    <img
      src="./img/logo-white.png"
      alt="logo of a white crown"
      class="header__logo"
    />
  </div>

  <div class="header__text-box">
    <h1 class="heading-primary">
      <span class="heading-primary--main">Outdoors</span>
      <span class="heading-primary--sub">is where life happens</span>
    </h1>

    <a href="#" class="btn btn--white btn--animated">Discover our tours</a>
  </div>
</header>
```

We have added the block name `header` and you can see how the elements of the `header` block got double underscore like `logo-box, logo, text-box`

Decided to keep `heading-primary` as its own block instead of making it an element of the `header` block so we can re-use it elsewhere.

notice stuff like `heading-primary--main, heading-primary--sub, btn--white, btn--animated`

They use double hyphens because they are modified versions of those blocks
