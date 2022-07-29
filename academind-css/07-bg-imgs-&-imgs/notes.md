# 07. Images and BG Images 

We have graduated the basics section. We are now in the advanced section. 

## Content 

- background property 
- using images and background images 
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


