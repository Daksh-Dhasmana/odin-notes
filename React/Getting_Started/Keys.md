# What is Keys
- A Key is a unique identifier that gives React a stable identity for each item in a list, enabling React to efficiently track which items have been added, changed, updated, or removed when the UI re-renders.
- In short, Key is like a unique identifier that is attached to a item, so it becomes easy to track it when later on we need to delete modify or do other operations
  
# Why do we need Keys in React
- We need keys in React so its Virtual DOM can assign a unique identity to each list item, allowing it to precisely track which items are added, updated, reordered, or deleted across re-renders
- Instead of wastefully recreating the entire list in the real browser DOM whenever data changes, React uses these stable keys to compare the old and new lists and update only the exact elements that actually changed.
- So, for analogy, Keys in React are exact same thing as id in HTML/CSS.
- A Parallel Analogy
-   | Feature | HTML/CSS `id` | React`key` |
    |---| ---| --- |
    |What is it?| A unique tag given to an element.| A unique tag given to a component/element.
    | Why use it?| So CSS/JS can pinpoint and target one exact element on the page. | So React can pinpoint and target one exact element during re-renders.
    |Rule|Must be unique among elements.|Must be unique among sibling items in a list.