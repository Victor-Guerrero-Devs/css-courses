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



