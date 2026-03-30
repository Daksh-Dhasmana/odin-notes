- To revisit grid, refer to [Grid](./Grid.md)
## Advanced Grid Properties

### repeat()
- is a function that acts as a shorthand for defining multiple tracks of same size.
- eg: `grid-template-column: 150px 150px 150px 150px 150px ` can be written as `grid-template-column: repeat(5,150px)`.

### Fractional unit
- They are used to make Grids "dynamic".
- The most common unit is `fr`.
- The `fr` unit is the way of distributing whatever remaining space is left(excluding gap unlike %).
- when using `fr`, all the grid-items fill the whole space unlike static