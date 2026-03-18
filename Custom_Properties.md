### Custom Properties
- They can be a big help when writing CSS as once declared, we can use them as many times we want.

## Declaration Syntax
- `--variable-name:value`, here property value can be any CSS value.
- It is a good practice to declare these custom properties globally like:-
  `:root{--variable-name:value}`. since it is declared globally.

## Usage Syntax
- class name: bor
- `.bor{ background-color: var(--variable-name)}`.

## Media Queries
- `@media()`
- is a logical expression used in CSS to apply styles based on device characteristics, such as viewport, theme etc.
- it's changing style of browser based on user's device configs.
- eg: prefers-color-scheme.
- It's like the "If" statement of CSS.
## Prefers-color-scheme
- `prefers-color-scheme`: is a type of media queries that detects system theme(like dark mode).
- `/* 1. Your default Light Mode styles */`
`:root {`
  `--bg: white;`
  `--text: black;`
`}`

`/* 2. The Media Query for Dark Mode */`
`@media (prefers-color-scheme: dark) {`
  `:root {`
    `--bg: #121212;`
    `--text: #ffffff;`
  `}`
`}`

`/* 3. Apply the variables */`
`body {`
  `background-color: var(--bg);`
  `color: var(--text);`
`}`
- In above code there are 3 parts: The Registory(root), The Sensor(@media), The application(body)
- in The Registory, we declare containers because if user doesn't have a preference then this will load
- in The Sensor, @media asks the OS about the condition(here if OS is set to dark mode). If yes then code inside is executed, if no then it's ignored. light value for media query is when user has light mode preference or no preference at all.
- In The Application, the code is then applied.