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

## CLI Intro

We need the CLI to compile our SCSS files into CSS ones. 

Here are the basics you should be able to do: 
- navigate through directories
- able to see what's inside directories 
- using tab for auto-complete naming on directories/files 
- moving out of directories 
- adding new files 
- deleting files 
- creating directories 
- deleting directories 

## Setting up SASS

This will be for any project in the future. 

1. have node and npm installed 
2. download sass globally `npm install -g sass`
3. make a directory called `sass-test`
4. within `sass-test` make an `index.html` alongside two more directories `sass` and `css`
5. within `sass/` make `styles.scss` and within `css/` make `styles.css` (make sure to link to the `css` file on `index.html`)
6. write some nonsense in `index.html` and then write some styles in `sass/styles.scss`
7. save everything 
8. in the terminal, in directory `sass-test`, write the command `sass sass/index.scss css/styles.css`
9. with that command, you compiled all the `scss` styles into `css/styles.css` and you should see plain old css in that file which the browser can understand. 

### Setting up SASS for Natours

1. make a new directory in `Natours/` called `sass/`
2. withing `sass/` create `main.scss`
3. copy everything within `css/style.css` and paste it into `sass/main.scss` (regular css works fine in scss files) 
4. any future css will be written in `sass/main.scss`
5. make sass variables out of the colors in the comments and save 

```css 
$color-primary: #55c57a;
$color-primary-light: #7ed56f;
$color-primary-dark: #28b485;
```
6. compile it into regular css like this `sass sass/main.scss css/style.css`
7. that's it, you just need to run that command every time changes are made 

There are scripts to do this for you automatically but w/e 

You can open a separate terminal open to your current project directory and run 

`sass sass/main.scss css/style.css -w`

The `-w` means watch so anytime a change is made and saved in `main.scss` it will be compiled into `style.css`

Be aware, the terminal can do nothing else while it is watching this which is why I told you to open a terminal just for thi job 

## Auto reload page on file changes

`npm i live-server -g`

Install live server globally 

Navigate to your project directory 

`live-server`

A new page will open on your default browser that will refresh itself on file change. 

This comman will also hog your terminal so you won't be able to do anything else on it (therefore 2 terminals that'll be too busy to doo anything else) 
