# 4. Intro to SASS and NPM

## Contents

- what SASS is
- how to use it in our project
- how to compile SASS files into CSS ones using npm

## What is SASS?
 
- CSS preprocessor
	- https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor

- let's you write CSS in an easier way especially for larger projects
	- CSS by itself can get very messy after a certain point 
- is converted into regular CSS by a SASS compiler 

There are many other CSS preprocessors but SASS is the most popular one. 

### SASS Features 

- variables 
- nesting selectors inside of each other 
- operators 
- partials & imports
- mixins 
- functions
- extends 
- control directives 

### SASS vs SCSS syntax 

SASS syntax doesn't use curly braces and relies exclusively on indendations 

SCSS syntax uses both curly braces and indendations so it is much easier to 
use. 

Use SCSS syntax instead. 

## First Steps w/ Sass

- open up codepen 
- switch the settings to use SCSS 
- now you can play around with it without the need of installing and configuring it on your local machine

https://sass-lang.com/guide

Read the docs to understand the syntax (not hard) 

If anything, the hardest thing to do will be installing and configuring it :( 

## Mixins, Extends, Functions

### Mixins

Mixins are basically snippets you can reuse just calling the mix-ins name. 

https://sass-lang.com/documentation/at-rules/mixin

You can practice the DRY principle by enclosing stuff you will be repeating a lot into a mixin and then bringing it into another selector with `@include mixin-name;`

### Functions

https://sass-lang.com/documentation/at-rules/function#plain-css-functions

Basically lets you do mathematical operations and return that value into a property like 

```css
@function divide($a, $b) {
  @return $a / $b;
}

nav {
  width: divide(60, 2) * 1px;
}
```

### Extends

https://sass-lang.com/documentation/at-rules/extend

It's basically a corrector in abusing BEM.

```html
<div class="error error--serious">
  Oh no! You've been hacked!
</div>
```

We have learned that a modifier to a block gets two dashes. Therefore, we need to create two selectors for this 

```css
.error {
  border: 1px #f00;
  background-color: #fdd;
}

.error--serious {
  border-width: 3px;
}
```

Extends helps us remove the class bloat from html elements. An example would be from the first HTML snippet. By using extends, we would just need one class `error--serious`

```css
.error {
  border: 1px #f00;
  background-color: #fdd;

  &--serious {
    @extend .error;
    border-width: 3px;
  }
}
```

IN regular CSS, it looks like: 

```css
.error, .error--serious {
  border: 1px #f00;
  background-color: #fdd;
}
.error--serious {
  border-width: 3px;
}
```

As you can see, `.error-serious` gets the same styles as the block as well as those as a modifier so we can get away with this 

```html
<div class="error--serious">
  Oh no! You've been hacked!
</div>
```

