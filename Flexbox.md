# Flexbox
- Flexbox is a way to arrange items into rows/columns(NOT LIKE A TABLE!!).
- These items will "flex"(grow, shrink) based on some rules.

## Flex container and Flex item
- A Flex Container is any element that has `display:flex;` on it.
- A Flex Item is any element that lives inside of an flex container.

## Flex Shorthand
- The `flex` declaration is usually a shorthand for 3 properties you can set on an flex item
- They are grow,shrink, basis.
- Example: flex:1 is shorthand for flex-grow:1, flex-shrink:1, flex-basis:1.

### Flex-basis
- Defines initial size of item before "flexing" occurs.
- Behavior: It sets the "base" size. If flex-direction is row, it acts like width. If column, it acts like height.
- Values: Can be a specific measurement (e.g., 200px, 20%) or auto (which uses the item's content size).
- Key Fact: The browser looks at flex-basis first to calculate how much room is left in the container.

### Flex-grow
- This defines the ability of a flex item to expand if there is positive free space in the container.
- Logic: It accepts a unitless number that serves as a proportion.
- Calculation: If Item A has `flex-grow: 1` and Item B has `flex-grow: 2`, Item B will take up twice as much of the remaining empty space as Item A.
- 