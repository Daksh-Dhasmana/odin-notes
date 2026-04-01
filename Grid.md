# Grid
- They are like normal grid.
- Similiar to [Flexbox](./Flexbox.md) but unlike Flexbox(1-D), grid is 2D.

## Grid Container
- They contain Grid.
- The items inside it are called grid items.
- An element can be turned into grid using `display:grid` or `display:inline-grid`.
- NOTE: ONLY THE DIRECT CHILDREN ARE GRID ITEMS NOT GRANDCHILDREN.
- Grid items can also become Grids themselves.
- Use `display:grid` when you want a Structure or a Section
- Use `display: inline grid` when you want a "Widget" or a "Component" that shouldn't break the flow of your text.

## Grid Tracks
- Is the space between two grid lines

## grid-template-columns and grid-template-rows
- Arranges element into rows and colums
- It can have various values like px, percentage, fractional units etc.
- They are defined inside the grid container

## Shorthand for grid-template
- Defines grid size
- Defines how many rows and columns should be there in a grid.
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

## Positioning Grid Elements
- The line numbering is from left to right and top-to-bottom flow.(Important for positioning).

### Grid-column-start/end and Grid-row-start/end 
- Defines the grid line where item begins(start) and where item ends(end).
- To calculate the `end` you must calculate the lines not the boxes.
- eg:-if you want an item to span 2 columns, then it must start at line1 and end at line 2.
- Shorthand:- `grid-column: [start]/[end]`, `grid-row: [start]/[end]`.

### Grid-area
- Is a short hand for grid-column and grid-row.
- Shorthand: `grid-area: [grid-row-start] [grid-column-start]/ [grid-row-end] [grid-column-end];`
- eg:
`.container {`
`  display: inline-grid;`
`  grid-template: 40px 40px 40px 40px 40px / 40px 40px 40px 40px 40px;`
  `background-color: lightblue;` 
  `grid-template-areas: `
   `"live live live live live"`
   `"live live live live live"`
   `"bed bed bat kit kit"`
   `"bed bed bat kit kit"`
   `"close close bat kit kit";`
`}`

`.room {`
`  border: 1px solid;`
  `font-size: 50%;`
  `text-align: center;`
`}`

`#living-room {`
  `grid-area: live;`
`}`
`#kitchen{`
  `grid-area: kit;`
`}`
`#bedroom{`
  `grid-area: bed;`
`}`

`#bathroom{`
  `grid-area: bat;`
`}`
`#closet{`
`  grid-area: close;`
`}`

- for advanced grid properties refer to [Advanced_Grid_Properties](./Advanced_Grid_Properties.md)
