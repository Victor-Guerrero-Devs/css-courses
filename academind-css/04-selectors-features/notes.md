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

### CSS Class Selectors vs ID Selectors 

90% of the time, you should be using classes to style HTML elements. 

Ids should be reserved for targetting elements in JS or for linking to sections 
on your webpage. 
- since you can only use IDs once, they can also be used to mark the main container 
of a section on your webpage, e.g. `<section id="product-overview">`

### !important 

- used to override specficity 
- normally should be avoided or you'll end up with spaghetti CSS 

```css
a { color: white !important; }

a.highlighted { color: yellow; }
```

Normally, `a.highlighted` would take priority for the color property because it has higher 
specificity but, since we added `!important`, `a` takes priority 

### The Pseudo-class :not()


```css
a:not(.highlighted) { color: white; }

a.highlighted { color: yellow; }
```

The first selector is targetting every anchor element that does not have the `highlighted`
class. 

This is all `:not()` does. Whatever it has in its parantheses, it will not target it. 

Generally, you should just use specficity instead of `:not()` because of preformance as well 
as readability 

```css
a { color: white; }

a.highlighted { color: yellow; }
```

This does the same job as the first snippet but better. 

Nevertheless, there are some specific cases in which `:not()` is very useful. 
