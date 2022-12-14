# 7. Trillo - Master Flexbox 

## Flexbox Philosophy

Instead of using floats and tables like we did in the last project, flexbox allows us to make flex containers which in turn can align the items inside EASILY. 

## Trillo - Project Overview 

We will build the UI for a webapp for checking out hotels. 

Obviously, it doesn't work; it's just for design practice. 

We will be using SASS once again but a lot more stripped down (our sass directory will not use the 5-1 architecture from the last project. just 4 separate scss files) 

## Project Settings and Custom Properties 

Since this project is just for flexbox, we will not use the fancy directory architecture from before. 

We just need 4 scss files and they all go inside of `/sass/`

Now for SASS variables vs CSS variable or custom properties. 

CSS variables are a recent addition and are better than SASS variables so we will use those instead. 

within `_base.scss` we add these global resets

```scss
* {
    margin: 0;
    padding: 0;
}

*,
*::before,
*::after {
    box-sizing: inherit;
}

html {
    box-sizing: border-box;
    font-size: 62.5%;
}
```

And in the same file we make a bunch of color variables in `:root { }`

## Overall Layout

```html
<div class="container>
  <header> ... </header>
  
  <div class="content">
    <nav class="sidebar"> ... </nav>
    <main class="hotel-view">
      <div class="gallery"> images go here </div>
      <div class="overview"> </div>
      <div class="detail"> 
        <div class="description"> </div>
        <div class="user-reviews"> </div>
        <div class="cta"> </div> 
      </div>
    </main>
  </div>
</div>
```

Basicall all of these divs are flex containers nested inside flex containers to achieve the layout. 

we set `.content` to flex display and so the two main flex items `nav.sidebar` and `main.hotel-view` are now aligned as a row. 

in order to get `nav.sidebar` to take up the exact width we want it to, we use 

```css
.sidebar {
  flex: 0 0 18%;
}
```

what this means is flex growth and shrink are set to zero (meaning we dont want it to grow or shrink in relation to the available space in the container) and it will always take up 18% of its container's width 

## Header 

Use flexbox to align the logo, search bar, and icons 

Use SVG sprite for icons 
- sometimes using icons for 3rd part libraries like font awesome aren't that great 
- although im skeptical about this claim given how popular it is to use them 
- this guy is saying that sometimes their servers can go down and your website will be left with empty icons 

https://icomoon.io/
- can download svg icons 
- can convert icons to svg 

How to use: https://icomoon.io/
- pick an icon library 
- select the icons you want 
- download them as zip 
- `symbol-defs.svg` = sprite 

Actually, refer to Mosh's section on SVGs and sprites. For some reason they arent showing up. 

## Header pt 2

Arrange the the logo, search bar, and user icon notifications w/ flex 

## Header pt 3 

Use flex again to make the icons on the right end of the header fall into a row and add space between them 

Used absolute positioning to place the notification number OVER the icon 

## Hotel Overview pt 1

- how to create an infinite animation 
- how to use `margin: auto;` w/ flexbox 
- more flex properties for ez alignment 

### .gallery

here we place three images as shots of various hotels 

they sit on top of everything else as a banner in a row

set the images to `display: block;` so they fill their entire flex item container 

### .overview

This is basically the title section where you have the hotel name, location, and rating 

Very slim row, use flex to align them 

as for the **infinite animation**, this will be applied to `<button class="btn-inline">Albufeira, Portugal</button>` which will make it pulsate as long as the mouse is hovering over it 

```scss
&:focus {
        outline: none;
        animation: pulsate 1s infinite;
    }
```

This is the nested selector for `.btn-line` that provides the infinite animation 

## Hotel Overview pt 2

Now that the structure is made, style the typography, the icons and clean up the alignment/padding/margins 

## Description Section pt 1

This section is broken into three mini sections
- description of hotel 
- user reviews 
- cta for booking it 

Therefore `.detail` is a flex container that has three items. 

## Description pt 2 

style `.description`

## User Reviews

Here we style the user reviews section 

This flex container has 3 main items: 2 reviews and a button for showing more. 

the reviews also contain a flex container, not for the quote, but for the picture of the reviewer, the reviewers name, and finally their score 

## CTA Section

Basically, I moved `<div class="cta">` outside of `.detail` b/c it was orginally sharing the same row as the other 2. 

By making `cta` a sibling of `detail` instead of a child, i fixed the alignment problem. Now CTA has its own row 

Anyway, the btn has two spans within it. Only one of them is visible at a time. 

When the user hovers over the btn, the visible text moves off screen while the invisible ones moves back onto the screen. 

```scss
.btn {
  &__visible {
        padding: 2rem 7.5rem;
  }

  &__invisible {
        position: absolute;
        padding: 2rem 0;
        left: 0;
        top: -100%;
  }

  &:hover {
        background-image: linear-gradient(to left, var(--color-primary-light), var(--color-primary-dark));
  }

  &:hover &__visible {
        transform: translateY(100%);
  }

  &:hover &__invisible {
        top: 0;
  }
}
```

## Media Queries 

Flex makes creating responsive websites easily. IN the first project when we weren't using flexbox, we needed a lot of css bloat to get things right. 

Flex requires so much less to get the layout you want. Sometimes it is as easy as changing to property to `flex-direction`

There are only two major changes for mobile/tablet viewports

1. the main container that is the parent of everything changes flex-direction to column, making the side navbar go on top of everything 

2. the detail section which has two columns becomes one column, i.e. instead of the hotel description and reviews being side by side, they go on top of each other 

Lastly breakpoints are made with the unit `em` to ensure things work as intended. 

## Conclusion

as of 2022, flexbox is available on 99% of browsers although IE does not currently support gap. 

finally, use the moshify method to bundle your project files to be production ready 
