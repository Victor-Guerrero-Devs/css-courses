# 13. Flexbox

You have made into Expert track

## Content

- flex container
- flex items
- main vs cross axis

## Flexbox Benefits

As already seen, we had to use some hacky methods to get items aligned to where we wanted them to be in their containers.

We used stuff like `inline-block`, `vertical-align`, `calc()`

We can instead use flexbox for a much easier experience and cleaner CSS.

## Understanding Flexbox

1. apply `display: flex;` to a container
2. all of the elements nested within it are now `flex-items`
3. you can now arrange the items easily

## flex-order

This property is used within flex-items.

All flex-items have this property set to 0 therefore they appear in the order in which they are declared in the HTML file.

If you were to change one of them to `flex-order: 1;`, it will automatically be the last one (b/c all of them are at 0)

If you were to change one of the to `flex-order: -1`, it will automatically be the first one (same logic).

## align-self

This property is used within flex-items and overrides whatever is in `align-items` within the flex container.

Therefore it works off the cross axis (vertical in rows, horizontal in columns)
