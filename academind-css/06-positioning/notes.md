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
}
```



