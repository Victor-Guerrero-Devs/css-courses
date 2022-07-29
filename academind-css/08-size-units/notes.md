# 08. Size Units (Theory)

## Contents 

- % 
- min-width vs max-width (for responsiveness) 
- rem vs em 
- vw and vh 


## min-width/height & max-width/height 

You use these to set a limit to how big or small an element may get. 

Typical Usage: 
- setting a max-width to a content container so it won't become stretched out on super wide monitors, e.g. `max-width: 1200px;` 
- setting a max-width to images so they don't grow out of proportion

```css
.customer-img {
  width: 100%; 
  max-width: 580px;
}  
```

In this snippet, the image will grow along with the size of its container 
until it reaches 580px in width. At that point, it will not grow anymore. 

Generally, you give the `width` and `height` property a % unit but give the min and max variants a fixed unit, i.e. pixels 

This will ensure that your elements have limits to how small they can get on mobile devices and how big on super wide monitors/tvs 

This is essential for responsive design

## em vs rem 

em is too much of a headache so avoid using it. 

stick to rem b/c 
- responsive to the user's browser font settings 
- overall responsive 

use `rem` especially for font-size and if you wish for padding and margin as well 
- if you do use it for padding and margin as well, these will also be responsive 
to the user's browser font size setting 
- nevertheless, not necessary to aim for that much responsiveness 
- it is equally fine just to use pixels for margin/height 

**Conclusion:** use rem for font-size (and maybe padding/margins) and pixels for anything else 
