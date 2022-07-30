# 09. CSS with JS

Sometimes, you may want to change styles AFTER the page has been loaded. JS allows you to do this easily. 

## Content 

- changing CSS classes on elements w/ JS 
- manipulating CSS styles on elements directly 

## Adding a Modal 

Last section we created a backdrop. We will now use that whenever we click on the **CHOOSE PLAN** button on the main page. 

A modal will pop on top of the backdrop which asks the user if he/she wishes to proceed with the selection 

### Snippet 

#### HTML 
```html
<div class="backdrop"></div>
  <div class="modal">
      <h1 class="modal__title">Do you want to continue?</h1>
      <div class="modal__actions">
          <a href="start-hosting/index.html" class="modal__action">Yes!</a>
          <button class="modal__action modal__action--negative" type="button">No!</button>
      </div>
  </div>
```

Remember these two go right after the opening body tag before anything else. 

As you can also read from the markup, the modal consists of two things: a yes and a no button 

#### CSS
```css
.modal {
  position: fixed;
  display: none;
  z-index: 200;
  top: 20%;
  left: 30%;
  width: 40%;
  background: white;
  padding: 1rem;
  border: 1px solid #ccc;
  box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.5);
}
```

This is the styling for the component. As you can see, we use the fixed position to make sure if lays on top of everything else (notice z-index as well) and to position it near the center 

## JS Intro 

As stated before, JS allows us to change not only the CSS applied to our HTML elements but also the HTML elements themselves. 

This is so b/c JS executes after the browser has loaded our HTML file and we can use JS to work with the DOM, i.e. the browser's virtual representation of our HTML file. 

Therefore, w/ JS, we will change the display property of our backdrop from none to block

## Making it work 

1. make variables of the backdrop element and modal 
2. make a node list variable for the plan buttons 
3. run a for loop for the node list 
4. add an event listener to each one that changes the display to block for both the backdrop and modal 
5. make another variable for the no button on the modal 
6. make an event listener for the no button after the for loop
7. if clicked, switch the display back to none for both the backdrop and modal 
  - if the yes button is clicked, (remember it is an anchor element) the user will just be taken to a new page (which will be made later) 
  
## Mobile navbar HTML and CSS

Later in the course, we will pretty this up when we make the site mobile friendly. 

For now we will implement the hamburger and the navbar

### Hamburger HTML 

Add this in the `.main-header` in front of `main-header__brand`

```html
<div>
  <button class="toggle-button">
    <span class="toggle-button__bar"></span>
    <span class="toggle-button__bar"></span>
    <span class="toggle-button__bar"></span>
   </button>
   <a href="index.html" class="main-header__brand">
      <img src="images/uhost-icon.png" alt="uHost - Your favorite hosting company">
    </a>
</div>
```

### Hamburger CSS 

This goes in `shared.css`


