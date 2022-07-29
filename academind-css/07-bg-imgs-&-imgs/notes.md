# 07. Images and BG Images 

We have graduated from the basics section. We are now in the advanced section. 

## Content 

- background property 
- using images and background images 
- add a customers page
- gradients 
- filters 

## Background property 

This is a shorthand property. You can use multiple values in it but it is advised to use 
the regular properties to control these things. 

`background` is the short hand for all of these 
	- `background-image`
	- `background-color`
	- `background-repeat`
	- `background-size`
	
There are many more and you can find them here: https://developer.mozilla.org/en-US/docs/Web/CSS/background

### Container Background Image 

```css
#hero-section {
  background-image: url("imgs/hero-img.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}
```

The property `background-size: cover;` makes sure that the image fills the entire container and maintains its ratio, i.e. won't stretch out 

An equivalent to that would be `background-size: 100%;` which says the image will take up 100% of the container's width 

`background-size: 500px 200px;` you can also pass a second value which affects the height therefore this means the image will be 500px wide and 200px tall 

### background-position

Imagine you have a large painting and a sqaure frame. The painting is bigger than the frame so some sacrifices will have to made. 

With this property, you can decide which part of the image will be sacrificed in order to fit into the frame. 

https://developer.mozilla.org/en-US/docs/Web/CSS/background-position

### background-origin 

https://developer.mozilla.org/en-US/docs/Web/CSS/background-origin

You can determine the image's border
 - does it start with the container's outside border? inside border? content border? 
 
## New Page: Customers

Here we will add our testimonials with images from our "customers" 

Create a directory called `customers` and create a new html file within it 

As with the package page, copy and paste the header and footer HTML into the new customers page.

We will also create a new CSS file for styles specific to the customers page in the same directory 

### Customer images 

First we wrap them in a div with the class `testimonial__image-container`
- the image container should take up 70% of their testimonial container 

THe images themselves have the class `testimonial__image`
- have the images take 100% of their image container 

Give them a box shadow to give get the 3-d look 


## Gradients 

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients

You can use these gradients to replace background images

In a sense, they are a fancier version of using `background-color: red;`

Instead you would use `background-image: linear-gradient(red, white);`

Besides linear gradients, you can also use radial gradients which lets you make more complicated color transistions 

## Stacking Backgrounds 

It is possible to stack multiple bg images, solid colors, and gradients as the same background. Only one of the bg images can show up at a time however. 

Usually, solid colors are used as back ups should the image fail to load. 

Gradients are usually used with bg images to give them give them an overlay (make sure to use `rgba()` for the color so you can tweak the opacity) 

## Filters

https://developer.mozilla.org/en-US/docs/Web/CSS/filter

CSS now has the power of PhotoShop (to some extent) 

We can use CSS to apply filters to images without the need of photoshop. 

One of the most popular ones is `filter: grayscale(X%)`
  - mainly used on bg images for containers to give more contrast to the text content 
  - 100% = straight up black and white 
  - 0% = zero change 
  

