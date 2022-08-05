# 6. Natours Responsive Design

The final module to the Natours project. We implement responsive design to it. 

## Intro 

So far, we have been building this project desktop-first. This is not how websites are generally developed these days. Instead, most start designing for mobile first and then using media-queries to accomodate tablets, laptops, and desktops. 

### Benefits of mobile-first design

- most internet users are mobile users 
- reduces bloat for the mobile experience 
- easier to design for mobile b/c there is less room to work with 

### Cons of mobile-first design

- does your userbase primarily use mobiles? 
- desktop version may look too bare 
- more constrained design choice 

### Breakpoints

Bad Breakpoints
- using the widths of the latest iPhone, iPad, mac, etc 
- everytime a new version comes out, you'll need to change your break points 

Good Breakpoints 
- using the average widths of the most popular phones, tablets, laptops 

Best Breakpoints 
- making breakpoints designed around your layout 
- whenever your layout break, you make a new breakpoint to fix it 

https://www.browserstack.com/guide/ideal-screen-sizes-for-responsive-design

According to this, the 3 most popular resolutions in 2021 were: 

1. 1920x1080 
2. 1366x768
3. 360x640

## SASS + Breakpoints 

The best way to add media queries with SASS is by using mixins. 

You would think that the best way is to go into the individual components in `sass/components/` and add media queries directly inside the selectors 
- this is the same idea as in Mosh's course where he added a media query at the end of every component/section specific to that thing 

However, this is troublesome and will be a pain to edit all of them should the need arise to do so. 

This is where mixins come in. 

Go to `/sass/abstracts/_mixins.scss` to see the media queries. 

```scss
@mixin respond($breakpoint) {
  @if $breakpoint == phone {
    @media only screen and (max-width: 37.5em) {
      @content;
    } //600px
  }
  @if $breakpoint == tab-port {
    @media only screen and (max-width: 56.25em) {
      @content;
    } //900px
  }
  @if $breakpoint == tab-land {
    @media only screen and (max-width: 75em) {
      @content;
    } //1200px
  }
  @if $breakpoint == big-desktop {
    @media only screen and (min-width: 112.5em) {
      @content;
    } //1800
  }
}

```

## Typography and Layout media queries

we will update the typography and layout scss files to include our media queries 

```scss
.heading-secondary {
  font-size: 3.5rem;
  
  ...
  
  @include respond(tab-port) {
    font-size: 3rem;
  }

  @include respond(phone) {
    font-size: 2.5rem;
  }

}
```

this is from `/sass/base/_typography.scss` and show how we use the `@include` keyword plus the media query width "variable" with the property we wish to change inside

As for layout, we reduce the amount of columns as the viewport width grows smaller 

## About and Features Section

meh 

## Tours, Stories, Booking Sections 

meh

## Overview on Responsive Images

Why use responsive images? Mainly for performance concerns. You don't want to waste someone's mobile data by having them download 1mb desktop images when you could use 200kb mobile images instead. 

Secondly, performance again. You don't want a mobile user to have to wait 10 seconds to download all the assests from your page. 

### 3 use cases for responsive images 

1. resolution switching: decrease image resolution on smaller screens 
2. density switching: provide high res images for high density screens 
	- say we have an image that is 200px wide 
	- this same image displayed on a device with retina display will appear as 400px wide 
	- as a consequence, if it is not high res, the image will look stretched out and pixelated 
	- hence the need for density switching 
3. art direction: providing a modified image to smaller screens, e.g. most common usage is cropping 

## Putting Responsive Images in Action

```html
<img
  srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 1000w"
  sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
  alt="Photo 1"
  class="composition__photo composition__photo--p1"
  src="img/nat-1-large.jpg"
/>
```

In this example, we are using **resolution switching**. As you can see, a smaller img (300x200) is displayed on smaller viewports and a larger img (1000x667) on larger viewports 

Next to srcset, you see `300w` and `1000w`. This tells the browser the width of these images without needing to download them. The browser will decide. 

The smaller img is 37kb and the bigger one 370kb. Mobile users now save about 340kb of data. That's huge! 

```html
<picture class="footer__logo">
          <source
            srcset="
              img/logo-green-small-1x.png 1x,
              img/logo-green-small-2x.png 2x
            "
            media="(max-width: 37.5em)"
          />
          <img
            srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x"
            alt="Full logo"
            src="img/logo-green-2x.png"
          />
        </picture>
```

In this example, we use **density switching** and **art direction**. We provide a higher res logo for high density screens and a modified logo for mobile. 
- by modified, the logo is arranged in a row on mobile but as a column in bigger viewports thus art direction

## Responsive Imgs and CSS

- how to implement responsive imgs in CSS
- how to use resolution media queries to target high res screens 
- combining multiple conditions in media queries 

We are going to make the hero bg img responsive by making it smaller for mobile phones 
- you should try to implement this to the other imgs that are being used for the background as well, e.g. the features section, the form 

```scss
@media only screen and (min-resolution: 192dpi) and (min-width: 37.5em),
    only screen and (-webkit-min-device-pixel-ratio: 2) and (min-width: 37.5em),
    only screen and (min-width: 125em) {
    background-image: linear-gradient(
        to right bottom,
        rgba($color-primary-light, 0.8),
        rgba($color-primary-dark, 0.8)
      ),
      url(../img/hero.jpg);
  }
```

This is in `/sass/layout/_header.scss` and this is how we are able to change the bg img into a bigger one for desktop screens 

Currently, the default img is the one which is `1200px wide` which will look fine on mobile screens with 2x DPR 

We provide the larger version `2000px wide` for desktop viewports 

With these two options, we can save mobile users about 400kb in data while still giving them a sharp img if they have high density screens 

## Testing Browser Support 

The newer a CSS feature is, the more likely it is not supported by boomer browsers like internet explorer and safari. 

SASS provides some tools to get around this like `@supports (X) { }` which means if X is supported by the browser do this styling 

If X is not supported, those styles arent applied. 

Main concern is making the CSS work for safari by using web kits.

## NPM Build Process 

Since this course is like 5 years old, not gonna take exact notes. 

In any case, use NPM to compress your CSS/JS/HTML files and make them production ready. Find out the 2022 way to do this (mosh goes over this) 


