# Introduction to Keyboard Navigation
- Some users aren’t able to use a mouse to navigate or operate their computer, and by extension the websites they visit. 
- These users may instead rely on using a keyboard or another assistive technology that can simulate keyboard inputs, such as voice recognition software.
-  Other users may even just prefer using a keyboard over a mouse, or may use a mix of both. 
-  These users require proper keyboard navigation, something that can easily be overlooked when developing a website.

# Focus
- The point is that you need to make sure that any interactive elements are focusable by and have event handling for keyboards
- Using the correct semantic HTML can make this a lot easier of a goal to accomplish, but if you ever need to use an element that isn’t focusable or doesn’t have any event handling by default, then you need to add both of those functionalities in manually.

# Focus Styles
- Another aspect of focusable elements is their focus styles, which are usually an outline or border surrounding the element when it receives focus. 
- You should never completely remove focus styles. You should either leave these default focus styles alone, or you should replace them with your own focus styles. 
- Why? Completely removing focus styles can make a page impossible for keyboard users to navigate and operate, as they have no visual indication what element actually has focus. 
- It would force them to have to manually keep track of how many times they’ve pressed the Tab key while also trying to guess what elements are actually focusable.
- For example, imagine your cursor being invisible, you wouldn't know when to click or where's it's hovering.

# Tab Order
- The tab order is the order in which elements on the page will receive focus when pressing the Tab key, and is by default in the same order as the order of elements listed in the HTML file.
```
<!-- This element is first in the tab order. -->
<div tabindex='0'>This is the first element listed in the HTML.</div>

<!-- This element is second in the tab order. -->
<div tabindex='0'>This is the second element listed in the HTML.</div>
```
- We can also change order in which elements on the page will receive focus when pressing the Tab key, by using `tabindex`
- Like this
```
<!-- This element is first in the tab order. -->
<div tabindex='1'>This is the first element listed in the HTML.</div>

<!-- This element is second in the tab order. -->
<div tabindex='0'>This is the second element listed in the HTML.</div>
```
- Regardless of which method you may use, you should make sure the tab order matches the visual order of elements. 
- If the tab order is different from the visual order, users could be left confused or frustrated trying to navigate the page with a keyboard, expecting one element to receive focus based on the visual layout and instead another element receives focus.
- The best way to avoid this issue is to just place elements in your HTML file in the order that you want them to actually receive focus.

# Hidden Content
- Sometimes you want to hide some content until the event occurs like user clicking on a button to open a menu.
- When you want to hide content for this sort of purpose, you need to make sure the content is not only visually hidden, but also hidden from assistive technologies until that content is meant to be visible.
- If you don’t properly hide such content, then keyboard users would be able to tab into that content before they’re meant to, but in doing so they would lose track of any visual focus on the page. 
- solution is giving the container for the hidden content itself either the `display: none` or `visibility: hidden` CSS property when it’s hidden, and removing or overriding that property when it’s meant to be visible. 
- This not only removes the menu items from the tab order, but it also prevents assistive technologies from announcing them.

