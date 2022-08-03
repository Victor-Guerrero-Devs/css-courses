# 5. Natours w/ Adv CSS & SASS

Before beginning, open a terminal with two tabs that are in the project directory `2-nautours-intro/`

and run 

`sass sass/main.scss css/style.css -w`

and 

`live-server`

Let's get started!! (remember, in order to save space on github by not spamming a new project repo with 20mb of images, all changes to the project are in `2-nautours-intro/`)

## Converting our CSS into SCSS

Thanks to BEM, each element has its hyper specific class selector. Therefore, using SASS nesting isn't really necessary. 

Nevertheless, we will still use it.

Before 
```css
.header {
  height: 95vh;
  position: relative;
}

.header__logo-box {
  position: absolute;
  top: 4rem;
  left: 4rem;
}

.header__logo {
  height: 3.5rem;
}
```

After 
```css
.header {
  height: 95vh;
  position: relative;

  &__logo-box {
    position: absolute;
    top: 4rem;
    left: 4rem;
  }

  &__logo {
    height: 3.5rem;
  }
}
```

We use the `&` to stand in for the block, in this case `header`

Continue to do this for everything else on the page. 
