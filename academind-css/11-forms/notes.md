# 11. Forms

## Content

- style inputs and buttons
- validation feedback styles

## HTML Form

```html
<main class="signup-page">
  <h1 class="signup-title">Awesome! Let's dive right in!</h1>
  <form action="index.html" class="signup-form">
    <label for="title">Title</label>
    <select id="title">
      <option value="mr">Mr.</option>
      <option value="ms">Ms.</option>
    </select>
    <label for="first-name">First name</label>
    <input type="text" id="first-name" required />
    <label for="last-name">Last name</label>
    <input type="text" id="last-name" required />
    <label for="email">E-Mail</label>
    <input type="email" id="email" required />
    <label for="password">Password</label>
    <input type="password" id="password" required />
    <input type="checkbox" id="agree-terms" required />
    <label for="agree-terms"
      >Agree to
      <a href="#">Terms &amp; Conditions</a>
    </label>
    <button type="submit" class="button">Sign Up</button>
  </form>
</main>
```

## CSS Form

```css
.signup-form label,
.signup-form input,
.signup-form select {
  display: block;
  margin-top: 1rem;
  width: 100%;
}
```

Input eles are inline by default. Therefore we change them to block so each one stacks on top of the other

### attribute selectors

```css
.signup-form input[type="checkbox"] {
  border: 1px solid #ccc;
  background: white;
  width: 1rem;
  height: 1rem;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
```

With this, we select any input element inside of `.signup-form` that has the type checkbox. You can get more fancy with this but just look it up on mdn.
