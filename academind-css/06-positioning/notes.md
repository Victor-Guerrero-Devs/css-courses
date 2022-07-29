# 06. CSS Positioning  (Theory Module) 

## Content 

- the position property 
- navbars + fixed position 
- z-index 
- absolute and relative positioning 
- sticky positioning 

### position: static; 

- default for all elements. 
- means it can't be moved with the properties `top, bottom, left, right`
- position remains `static`, i.e. the same 

### position: fixed; 

- element is taken out of the flow 
- other elements move to compensate, i.e. the space is freed up and the others take over 
- now you can move this element anywhere on the viewport with `top, bottom, left, right`
- wherever it is, it sticks to it even if you are scrolling around 
- this is why it is popular to use on the navbar/heading 
- as long as you position it to the top, the navbar remains on top no matter how much 
the user scrolls down/up 

### fixed navbar snippet 

```css
nav {
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  margin: 0;
  box-sizing: border-box; 
  z-index: 1; 
}
```

make sure to increase z-index if any elements start going over the nav bar as you are scrolling down

### fixed bg img snippet 

- another popular use case is using it for bg imgs for sections 
- the trick is to reduce its z-index value so the other elements go on top 

```html
<section id="packages-overview">
  <div class="bg-img"> </ div> 
  <!-- rest of the elements go below --> 
</ section>   
```

- the bg img gets its own div container and goes on top of everything else 

```css
.bg-img {
  background: url("./images/blue_sky.jpg");
  width: 100%;
  height: 100%;
  position: fixed; 
  z-index: -100; 
}
```

- now that bg img will cover everything within the packages section with all the other elements sitting on top

## Absolute + Relative 

- absolute works liked fixed
- element is taken out of the flow and can be moved around with `top, bottom, left, right`
- however, you need to make sure the element's container uses `property: relative;` or that element will pop out of its container 
- it will treat the body element as its parent 

### building a badge for a package 

- as stated before, we need to set the package container to relative and the badge 
element to absolute 
- now we can move the badge around freely inside of the package container with `top, bottom, left, right`
- 
