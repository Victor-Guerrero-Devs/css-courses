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
