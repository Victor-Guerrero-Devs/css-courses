# 5. Natours w/ Adv CSS & SASS

Before beginning, open a terminal with two tabs that are in the project directory `2-nautours-intro/`

and run 

`sass sass/main.scss css/style.css -w`

and 

`live-server`

Let's get started!! (remember, in order to save space on github by not spamming a new project repo with 20mb of images, all changes to the project are in `2-nautours-intro/`)

## Converting our CSS into SCSS

Thanks to BEM, each element has its hyper specific class selector. Therefore, using SASS nesting isn't really necessary. 

Nevertheless, we will still use it.

Before 
```css
.header {
  height: 95vh;
  position: relative;
}

.header__logo-box {
  position: absolute;
  top: 4rem;
  left: 4rem;
}

.header__logo {
  height: 3.5rem;
}
```

After 
```css
.header {
  height: 95vh;
  position: relative;

  &__logo-box {
    position: absolute;
    top: 4rem;
    left: 4rem;
  }

  &__logo {
    height: 3.5rem;
  }
}
```

We use the `&` to stand in for the block, in this case `header`

Continue to do this for everything else on the page. 

## 7-1 CSS Architecture

This is the directory structure that is used on very large projects so that maintenance becomes a lot easier. It may be overkill for this project which is just a landing page but it is a perfect way to be introduced to it. 

### base/
first we make a directory like so `sass/base/` and make `_base.scss`

Within the base directory, you will put very basic styles like CSS resets, animations, typography etc 
- all partial files like this use the `_` as part of their naming convention 

To import these into the `main.scss` file, we just need to put this at the top 

`import "base/base"`

SASS understands this as `/base/_base.scss`

### abstracts/

here we put files that are not outputting any css like variables, mixins, and functions 

these use the same naming conventions `abstracts/_variables.scss`

### components/

here we put files for the styles of different components

same naming convention `components/_button.scss`

remember components are independent and re-usable anywhere on the project.  it is the layout which glues them together to make a section. 

### layout/ 

here we put files for the styles of different sections, e.g. the header, footer, navbar etc

same naming convention `layout/_header.scss`

### pages/ 

here we put scss files that pertain to a single page's style 

in this project we only have the landing page but in a real project it would have as many scss files per webpage 

`pages/_home.scss`

### the rest 

There are two other directories we will not be using 

1. themes/ 
  - here you store scss files that provide different themes like dark mode 
  
2. vendors/ 
  - here you store third party css files like bootstrap, animation libraries etc 
  
Therefore we will use the 5-1 architecture 

### conclusion 

import all the stuff into `main.scss`

```sass
@import "abstracts/functions";
@import "abstracts/mixins";
@import "abstracts/variables";

@import "base/animations";
@import "base/base";
@import "base/typography";
@import "base/utilities";

@import "pages/home";
```

then take all the stuff `main.scss` and place it into its relevant location that we have just created 

Example: move all the variables into `abstracts/_variables.scss`

Since we have the terminal compiling any changes from `main.scss`, any changes done to files that are imported into it will be reflected automatically w/ live server as well 

we dont need to run sass on the entire directory because all of the individual sass files should flow into `main.scss`


## 3 Principles of Responsive Design

1. Fluid grids and layouts: columns are used to divide content and the number of columns either increase of decrease in relation to the viewport width (use % instead of pixels)

2. Responsive images: images that use % as width for fluid expansion and higher resolution alternatives for high density screens

3. Media queries: use breakpoints to insert new styles 

### layout types

1. float: we will use this for the current project b/c (as of 2017) a lot of browsers do not support flexbox or grid 

2. flex: for 2nd project, perfect for 1-d layouts 

3. grid: for 3rd project, perfect for 2-d layouts 

## Custom Grid w/ Floats

As mentioned, we will build a grid using floats to ensure that our layout works on any old browser. 

See the code here: https://codepen.io/joaogeureri/pen/vYRRyzb

We basically use the `table` display with `float` and responsive widths to get it working 

## About Section 

Now that we have a grid layout, we can build the about section. 

stuff in `base/_utilities.scss` are for storing classes that serve 1 stylistic purpose, like Tailwind CSS 

```css
.u-center-text {
  text-align: center !important;
}
```

```html
<div class="u-center-text u-margin-bottom-big">
  <h2 class="heading-secondary">
    Exciting tours for adventurous people
  </h2>
</div>
```

As you can see, we add that utility class to a div so that the text inside can inherit that property.

### about section structure

the overall section has two columns. 

the main headings takes both of them. 

below the heading, you have one column with the text + learn more button and the other column has the pictures 

```html
<section class="section-about">
  <div class="u-center-text u-margin-bottom-big">
    <h2 class="heading-secondary">
      Exciting tours for adventurous people
    </h2>
  </div>

  <div class="row">
    <div class="col-1-of-2"> text stuff here </div>
    <div class="col-1-of-2"> imgs go here </div>
  </div>
</section>
```

### components/_button.scss

we add additional styles for the anchor button for `Learn more ->` here 

### components/_composition.scss

this is where we place our styles for the images and the hover effects 

the images are nested in a container that is set to `position: relative;` and then each image is given its own class so we can give it its own position via `position: absolute`

this is how we get the layered image look. 
