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

## Hero pt 2

### position logo

We need to add `position: relative` to `.header` so we can use `position: absolute` for the logo container.

This way we can position it exactly where we want it.

```html
<header class="header">
  <div class="logo-box">
    <img src="./img/logo-white.png" alt="logo of a white crown" class="logo" />
  </div>
</header>
```

```css
.logo-box {
  position: absolute;
  top: 40px;
  left: 40px;
}

.logo {
  height: 35px;
}
```

### position h1 text

to the header element, we nest

```html
<div class="text-box">
  <h1 class="heading-primary">
    <span class="heading-primary-main">Outdoors</span>
    <span class="heading-primary-sub">is where life happens</span>
  </h1>
</div>
```

We wrap the h1 in that div so we can use `position: absolute;` again so we can put right in the middle and remains there at any viewport

```css
.text-box {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

This is just a fancy way to do it. `top: 40%;` because the cut out portion from the clip-path makes the dead center look lower so we need to take that visual illusion into account.

## Creating Cool CSS Animations

how to create animations in CSS w/ `@keyframes` and `animation` property

We are going to build a fade in animation for the header text and eventually button when the page loads up

- remember the JS library we imported in Moshify for the animations?
- now we will build it ourselves, at least partially

```css
.heading-primary-main {
  display: block;
  font-size: 60px;
  font-weight: 400;
  letter-spacing: 35px;

  animation-name: moveInLeft;
  animation-duration: 1s;
  animation-timing-function: ease-out;
}

@keyframes moveInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100px);
  }

  80% {
    transform: translateX(10px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```

This is how we make animations. As you can see, the main heading text begins by coming in from the left (-100px) as its letters come into view (opacity 0 to 1).

By 80%, it overshoots its landing but then goes back to its proper place at 100% (personally I think that jerky movement is lame but w/e)

```css
.heading-primary-sub {
  display: block;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 17.4px;

  animation: moveInRight 1s ease-out;
}

@keyframes moveInRight {
  0% {
    opacity: 0;
    transform: translateX(100px);
  }

  80% {
    transform: translateX(-10px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```

Finally for the sub text, notice how we used the `animation` shorthand this time and all we had to do is switch the pixel values in the new animation to get the direction correctly

## Styling the Button Pt 1

we will learn:

- pseudo-elements/classes
- `::after` pseudo-element
- hover animation w/ `transition` property

So we will add an anchor element right below the text within the same container

```html
<div class="text-box">
  <h1 class="heading-primary">
    <span class="heading-primary-main">Outdoors</span>
    <span class="heading-primary-sub">is where life happens</span>
  </h1>

  <a href="#" class="btn btn-white">Discover our tours</a>
</div>
```

And now time to style the anchor element to look like a button

```css
.btn:link,
.btn:visited {
  text-transform: uppercase;
  text-decoration: none;
  padding: 15px 40px;
  display: inline-block;
  border-radius: 100px;
  transition: all 0.2s;
}

.btn-white {
  background-color: #fff;
  color: #777;
}
```

Now to position the button correctly, we need to go to `.text-box { }` and add `text-align: center;` so we can vertically center the button.

Next we need to go to `.heading-primary` and add `margin-bottom: 60px;` so we can add a 60 pixel buffer between the main heading and the button.

Now for the animation. Take note of `transition: all 0.2s;` -- this is the basic way of handling animations. We have already done the more complicated version with `@keyframes` and the `animation` property but sometimes that isn't necessary for every little thing.

```css
.btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.btn:active {
  /* active = when it is clicked */
  transform: translateY(-1px);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
```

Here we made some transitions that makes the button move up and produce a shadow (giving it a 3d feel) when it is either hovered or clicked.

## Animating the Btn Pt 2

First add a new class `btn-animated` to the anchor element acting as our button

Second make a keyframes for it

```css
@keyframes moveInBottom {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}

.btn-animated {
  animation: moveInBottom 0.5s ease-out 0.75s;
  animation-fill-mode: backwards;
}
```

Now when the page loads, the button on the hero section will seem to float from the bottom as it slowly obtains physical form
