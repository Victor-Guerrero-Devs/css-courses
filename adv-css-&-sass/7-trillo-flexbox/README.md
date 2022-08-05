# 7. Trillo - Master Flexbox 

## Flexbox Philosophy

Instead of using floats and tables like we did in the last project, flexbox allows us to make flex containers which in turn can align the items inside EASILY. 

## Trillo - Project Overview 

We will build the UI for a webapp for checking out hotels. 

Obviously, it doesn't work; it's just for design practice. 

We will be using SASS once again but a lot more stripped down (our sass directory will not use the 5-1 architecture from the last project. just 4 separate scss files) 

## Project Settings and Custom Properties 

Since this project is just for flexbox, we will not use the fancy directory architecture from before. 

We just need 4 scss files and they all go inside of `/sass/`

Now for SASS variables vs CSS variable or custom properties. 

CSS variables are a recent addition and are better than SASS variables so we will use those instead. 

within `_base.scss` we add these global resets

```scss
* {
    margin: 0;
    padding: 0;
}

*,
*::before,
*::after {
    box-sizing: inherit;
}

html {
    box-sizing: border-box;
    font-size: 62.5%;
}
```

And in the same file we make a bunch of color variables in `:root { }`


