# Grid
- They are like normal grid.

## Grid Container
- They contain Grid.
- The items inside it are called grid items.
- An element can be turned into grid using `display:grid`.
- NOTE: ONLY THE DIRECT CHILDREN ARE GRID ITEMS NOT GRANDCHILDREN.
- Grid items can also become Grids themselves.

## grid-template-columns and grid-template-rows
- Arranges element into rows and colums
- It can have various values like px, percentage, fractional units etc.
- They are defined inside the grid container

## Shorthand for grid
- Syntax: `grid-template: [rows]/[columns];`.
- Eg: `grid-template: 50px 50px/50px 50px;`

## Implicit Grid
- Implicit grid consists of rows and columns that browser creates automatically because you added more content than your explicit grid can hold.
- `grid-auto-rows: [value]`:- Sets height of any new rows created.
- `grid-auto-columns: [value]`:- Sets height of any new columns created.
- `grid-auto-flows: [value=row/column]`:- Tells browser to add new data to new rows(default) or new columns.
- `.container {`
  `display: grid;`
  `/* Explicit: 2 columns */`
  `grid-template-columns: 1fr 1fr;` 
  
  `/* Implicit: Any extra rows created will be exactly 150px tall */`
  `grid-auto-rows: 150px;`
  
  `/* Logic: If there's extra stuff, put it in a new row (default) */`
  `grid-auto-flow: row; `
`}`

## Gap
- In CSS, gap is modern way to create space between items.
- In design terms, they are called gutters(space between columns) and alleys(space between rows).
- Syntax: `gap: [row-gap] [column-gap]`.
- Works in both Flexbox and Grid.