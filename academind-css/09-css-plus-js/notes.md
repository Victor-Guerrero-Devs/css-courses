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

This is so b/c we can use JS to work with the DOM, i.e. the browser's virtual representation of our HTML file. 

Therefore, w/ JS, we will change the display property of our backdrop from none to block
