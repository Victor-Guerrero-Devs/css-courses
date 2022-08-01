# 17. Future Proof CSS

## Table of Contents

1. [CSS Modules](#css-modules)
2. [CSS Variables](#css-variables)
3. Vendor Prefixes
4. Browser Support
5. Polyfills
6. Getting rid of inconsistent browser styles
7. Naming CSS CLasses
8. CSS Frameworks

<div id="css-modules"></div>

## CSS Modules

https://www.w3.org/Style/CSS/Overview.en.html

Remember how we said CSS 3 will not upgrade to CSS 4 but just get new modules and have the present ones updated?

The link above shows the work people are doing for the latest modules etc. It provides documentation that goes into more depth than MDN.

<div id="css-variables"></div>

## CSS Variables

Already know about this.

```css
:root {
  --color-primary: #fff;
  --color-accent: #333;
}
```

You make variables inside of the `:root` selector so you can clean up any repeating values and have an easily maintainable CSS file since you just need to go to one place to make changes.

This is not limited to colors. YOu can use variables for heading font-sizes, weights, etc etc
