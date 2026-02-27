## Child and Sibling combinators##
 -`>`: child combinator. selects only the specified direct child of parent. leaves other grand children untouched
      -eg:- div > p{}
      -We can select grand children like div>div>div.
- `+`: Adjacent sibling combinator.
       Select the next/following sibling.
- `~`: General sibling combinator.
       Select the all sibling that are following the selected child 
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
 - `::before and ::after`: they are used to add content BEFORE and AFTER element but these "ghost-element" exists within the tag.
## Attribute Selectors ##
 - It simply targets attributes like src, href etc.
 - Has same specificity as classes and pseudo-classes(0,0,1,0).
 - `[attribute]`: used to target a general attribute. eg-[src]{ }.
 - `selector[attribute]`: is a way to find attribute that is inside their HTML tags. eg- img[src]{}.
 - `[attribute = ""]`: used to find a specific attribute value. eg- img[src="pups.jpg"].