# 2. Diving Deeper

## Content

- Box model
  - margin collapsing (the block element with the larger margin cancels out the smaller one's)
- Display property
  - `display: inline-block;`
    - element becomes inline but you can now adjust its width, height, etc like a block element
- Properties to remember

## Tips

We use `inline-block` to structure our navbar, i.e. brand on the left hand side and nav links on the right (as well on the same line)

- with flexbox, we can do the same job a lot easier
- nevertheless, this is the oldschool way
- we use `width: calc(100% - 54px);` in `.main-nav { }` to let the nav links take up all the space not taken up by the brand (i.e. 54px) thereby allowing them to stay on the same line (hacky but works for now)
