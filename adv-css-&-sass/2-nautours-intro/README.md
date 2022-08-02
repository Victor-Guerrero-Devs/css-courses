# 2. Natours Setup and 1st Steps

## Project Intro

We will be building a website for a fictional company that gives outdoor tours. We will build their landing page with a ton of modern CSS skills like mobile nav menu, animated cards, videos playing in the background etc.

## Hero pt 1

First, we need to make a header element w/ the class header

Second, we use the universal selector to get rid of any margin/padding and set box-sizing to border-box

Third, we set the general typography rules in body so the rest of the elements can inhiert them

Fourth, we apply the hero img as the background like so

```css
.header {
  height: 95vh;
  background-image: linear-gradient(
      to right bottom,
      rgba(126, 213, 111, 0.8),
      rgba(40, 180, 131, 0.8)
    ), url(../img/hero.jpg);
  background-size: cover;
  background-position: top;

  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
}
```

`background-image` property means: apply this linear gradient across the entire image but lower the opacity so the image can actually be seen

`background-position` = no matter the viewport width, the top of the image never changes

`clip-path` = add a sloping cut at the bottom border of the hero section. Look it up on MDN for more info. Btw websites exist to handle all of the nitty gritty.
