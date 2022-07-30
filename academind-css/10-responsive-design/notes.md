# 10. Responsive Design

## Content

- Hardware vs Software Pixels
- the viewport <meta> HTML in the <head>
- Media queries

## Hardware vs Software Pixels

The iPhone 8 has 375 hardware pixels in width, i.e. the physical amount of pixels on the screen.

This same iPhone has about 1124 software pixels in width, i.e. how those pixels physical pixels are translated in reality.

As you can see, the iPhone 8 has a DPR of 3, i.e. its software pixels are three times its hardware pixels.

This has its benefits like sharper images and text on a smaller screens.

This also has negatives like images looking bad if they are low resolution (although they may look fine on desktop).

Another problem is we usually set media queries for mobile at ~450px width. As a consequence, our media query will never activate on an iPhone 8 if its width is at 1125 pixels.

We can solve this with one simple meta tag.

## Viewport Meta Tag

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

With this simple addition (comes with the emmet boilerplate), our CSS will only take the hardware pixels into account instead of the software pixels.

## Media Queries

We use these in our CSS files to activate a style change at X viewport width.

It seems that using REM or EM over pixels is best because if a user has changed their default font-size via browser settings, breakpoints won't work as expected (i.e. they may fire off prematurely or late, thereby messing up the layout, depending if the browser settings for font size is smaller or larger than the default) if they are set with pixels instead of REM or EM.

Therefore use REM or EM when setting your media queries

### Good

```css
@media screen and (min-width: 45.375rem) {
}
```

That equals to 726px (typical tablet breakpoint)

### Bad

```css
@media screen and (min-width: 726px) {
}
```

## Breakpoints

Use this website: https://www.mydevice.io/ || https://screensiz.es/macbook-air-11-inch-late-2010-mid-2012

- lets you know about the specifics of your current device
- allows you to see the specs of modern mobile phones and tablets

Most modern mobile devices have a physical width of about 325 - 550 pixels.

Most tablets range from 726 - 1024 pixels

Desktop monitors 1660px+ width (mine is 1920px)

Laptops 1024 - 1660px width (can go above 1920px)

Since you should build for mobile first, your media queries should use `min-width`, i.e. when viewport width is at least X, and should have them for tablets, laptops, desktops and even smart TVs

start w/ video 152
