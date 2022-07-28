# 4. More on Selectors and CSS Features

## Content

- when to use CSS classes vs IDs
- !important
- pseudo classes vs pseudo elements
- :not()

### Multiple CSS classes 

- an HTML element may have multiple classes 
- if those classes target a specfic property like border, the class that is lower on the
CSS file will take priority. 
- therefore, the order the classes appear in the HTML element does not matter 
- what matters is which one is below the other in the CSS file

### Combined Selectors 

```css
a .active { }
```

- the above targets any elements with the active class nested within anchor elements 

```css
a.active { }
```

- the above targets any anchor elements that have the active class
