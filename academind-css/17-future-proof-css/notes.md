# 17. Future Proof CSS

## Table of Contents

1. [CSS Modules](#css-modules)
2. [CSS Variables](#css-variables)
3. [Vendor Prefixes](#prefixes)
4. [Browser-Support] (#support)
5. [Polyfills] (#polyfills)
6. [Inconsistent-browser-styles] (#inconsistent)
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

<div id="prefixes"></div>

## Vendor Prefixes

WHen a new CSS module is being developed, some browsers implement them before they are finished.

Let's say `transition` was a new thing

```css
.myClass {
  -webkit-transition: all 1s linear;
  -moz-transition: all 1s linear;
  -ms-transition: all 1s linear;
  -o-transition: all 1s linear;
  transition: all 1s linear;
}
```

Therefore, we wanted to make sure this new CSS feature would be supported across all the major browsers, we need to use all of those vendor prefixes.

When a new CSS module becomes finalized across all those browsers, we dont need the prefixes any more

```css
.myClass {
  transition: all 1s linear;
}
```

<div id="support"></div>

## Browser Support

https://developer.mozilla.org/en-US/docs/Web/CSS/@supports

Use that and caniuse.com to figure shit out. Avoid using the latest CSS beels and whistles.

`@support` allows use to use fallback styling if a browser does not support x feature

<div id="polyfills"></div>

## Polyfills

Polyfill is a JS package that enables certain CSS features that would otherwise not be supported by X browser.

Polyfill has its limits so not all features can magically be supported.

Also, it adds extra stress on the clients computer since it has to execute on their browser and affects the preformance of your page loading.

<div id="inconsistent"></div>

## Inconsistent Browser Styles

Two ways to handle this:

1. Use a reset library like `normalize.css`
2. Do it yourself with `*, *::before, *::after { }`
