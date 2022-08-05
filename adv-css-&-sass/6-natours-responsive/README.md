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

start here, vid 7
