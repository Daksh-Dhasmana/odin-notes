## Pseudo-Classes ##
-It is Dynamic  
-It changes properties of the selected element based on how user reacts to that element. like clicking a button makes that button red.  
-It is of two types:User/Dynamic pseudo-class and Structural pseudo-class.  
### Types of Pseudo-classes

1. **User Action Pseudo Class**
   - Makes site interactive and dynamic
   - `:hover`: Mouse over.
   - `:active`: Being clicked.
   - `:focus`: Selected via keyboard/mouse.
   - `:link`: for "unvisited" links
   - `:visited`: when a link is clicked 

2. **Structural Pseudo Class**
   - are way to select element based on their position in doc.
   - `:root`: every element in html doc comes under this. 
            :Why prefer this over body or html?:- because :root has more specificity/priority than both of them
            :Can be use to house global css rules to be used.
   - `:first-child`: The very first item in a list/div.
   - `:nth-child(n)`: Selects by number or pattern (e.g., `2n` for every second item).
   - `:empty`: target only those element who dont have any children.
   - `:only-child`: match element who dont have any siblings. FYI:sibling means sharing same parent.

## Pseudo Elements ##
 - They target/match parts of HTML which are not elements(which dont have closing tags). eg- <l1> <h1>
 - They share same specificity as normal elements. i:e, (0,0,0,1)
 - `::marker`: allow customization of <li> element's bullets or numbers. or a element having display: list-item.
               .Only <li> have this property.
 - `::first-letter and ::first-line` : give styling to first letter or first line.
 - `::selection`: change highlighting when user selects text on a page
 - `::before and ::after`:  