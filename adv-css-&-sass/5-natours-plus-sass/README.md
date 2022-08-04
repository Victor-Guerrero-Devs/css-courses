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

## Features section 

we will be using icons from https://linea.io/

Download it, copy over the fonts directory (where the icons are) and and the CSS file into your project's CSS directory. 
- rename the CSS file you downloaded to `icon-font.css` and link it on your index.html 

You can use the icons just by referencing its class name 

`<i class="icon-basic-compass"></i>` 

Add an additional class for styling 

### components/_feature-box.scss

this is where the styling for each features card will go 

It will also contain the styling for the icon as well as the hover effect which makes it bigger 

### pages/_home.scss 

we add a new selector for the `.section-features { }` and add general styles, the bg img with the linear gradient hue and the skew so we get the slopping borders like the hero on both the top and bottom 

```css
.section-features {
  padding: 20rem 0;
  background-image: linear-gradient(
      to right bottom,
      rgba($color-primary-light, 0.8),
      rgba($color-primary-dark, 0.8)
    ),
    url(../img/nat-4.jpg);
  background-size: cover;
  transform: skewY(-7deg);
  margin-top: -10rem;

  /* direct children of section features */
  & > * {
    transform: skewY(7deg);
  }
}
```

Notice in the direct children selector we skew everything in the opposite direction. This is how we achieve the sloping top and bottom borders of the section while the feature cards look normal 

## Tours section

90% of the styling done in this is found in `/sass/components/_card.scss`

Uses a rotating card effect to present info on the back of a card upon hover using `perspective` and `backface-visibility`

It looks like there are 3 cards but in reality there are 6. 

3 of them are the frontfeature-box and the other 3 are the back. Therefore, they come in pairs. The illusion that they are the same card comes from `absolute: position;`

In reality, they are stacked on top of each other and the back takes over on hover. 

`backface-visibility: hidden;` keeps the hidden card hidden 

## Story section 

aka Testimonials 

find the styles for this section in
- `sass/components/_bg-video.scss`
- `sass/components/_story.scss`

Simple section. We have a video playing as the background with two testimonial blocks and a button at the bottom. 

## Booking section 

This will cover styling forms, using the `::input-placeholder` pseudo-element, styles for invalid inputs and custom radio buttons. 

find the styles in
- `sass/components/_form.scss`

the general styles is in 
- `sass/pages/_home.scss`

The overall section has a linear gradient background 

The form component has the image of the lake as a background but has a linear gradient that covers the half which the actual input elements fall on 

```css
.book {
  background-image: linear-gradient(
      105deg,
      rgba($color-white, 0.9) 0%,
      rgba($color-white, 0.9) 50%,
      transparent 50%
    ),
    url(../img/nat-10.jpg);
  background-size: 100%;
  border-radius: 3px;
  box-shadow: 0 1.5rem 4rem rgba($color-black, 0.2);

  height: 50rem;
}
```

Found in `sass/pages/_home.scss`
