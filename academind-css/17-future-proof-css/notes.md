# 17. Future Proof CSS

## Table of Contents

1. [CSS Modules](#css-modules)
2. [CSS Variables](#css-variables)
3. [Vendor Prefixes](#prefixes)
4. [Browser Support](#support)
5. [Polyfills](#polyfills)
6. [Inconsistent Browser Styles](#inconsistent)
7. [Naming CSS Classes](#naming)
8. [CSS Frameworks](#frameworks)

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

Every browser has its default styles it likes to apply like margins to headers etc.

It is up to you to normalize these things.

<div id="naming"></div>

## Naming CSS Classes

There are a ton of naming conventions out there and the one you use will be up to you or your company.

A popular one you should get used to is BEM.

You use two underscores to name a component of a section

`.product-section__heading` = the heading within the product section

You use two dashes to name a new skin

`.product-section__heading--highlighted`

BEM = Block Element Modifier

`.block__element--modifier` = `.mobile-nav__link-item--cta`

The other big plus to using BEM is that the chances of you writing the exact same class twice is greatly reduced given how specific everything is.

<div id="frameworks"></div>

## CSS Frameworks

AKA Component libraries since they come with pre-styled components you can copy/paste into your own projects.

You also have utility frameworks like `tailwind` who provide you the tools to style components easily but you still have to do the work yourself.

### Benefits of Frameworks

- style your webpages very quickly
- follows best practices
- CSS lord not needed

### Downsides of Frameworks

- cookie cutter (although this could be mitigated by having your own stylesheet taking precedence like in Angela's Tindog project)
- a lot of bloat

### Benefits of Vanilla CSS

- full control
- little bloat

### Downsides of Vanilla CSS

- everything must be built from scratch
- danger of writing noob tier CSS
