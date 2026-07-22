# Transition
- CSS transitions let you animate a change from an element’s initial state to an end state
- `transition` is a shorthand property for transition-property, transition-duration, transition-timing-function and transition-delay.
- so
```
button {
  /* ... other CSS properties ... */
  transition-property: background-color;
  transition-duration: 1s;
  transition-timing-function: ease-out;
  transition-delay: 0.25s;
}
```
so `transition: [transition-property] [transition-duration] [transition-timing-function] [transition-delay]`
- We can write above in a shorthand for
```
button {
  /* ... other CSS properties ... */
  background-color: white;
  transition: background-color 1s ease-out 0.25s;
}
```
## Properties
### 1) transition-property
- This determines what CSS property will be transitioned. 
- In this case it is the background-color.

### 2) transition-duration
- This determines the duration that the transition will occur over. 
- In this case the color change will gradually happen over 1 second.
  
### 3) transition-timing-function
- his lets us change the speed of the transition over the course of its duration. 
- Here it will ease-out, meaning the color change will be faster at the start than at the end of the transition.
  - #### 1) ease (The Default): 
      - Starts a little slow, accelerates quickly in the middle, and then grinds to a gentle halt at the end. 
      - It feels very natural because most physical objects don't start or stop instantly.

  - #### 2) linear (Constant Speed): 
      - No acceleration, no deceleration. 
      - It moves at the exact same speed from the very first pixel to the last. 
      - This can feel stiff, but it's perfect for things like continuous spinning animations or color fades.

  - #### 3) ease-in (Slow Start): 
    - Starts completely slow and steadily builds up speed until it hits a sudden, fast finish. 
    - Think of a car stepping on the gas pedal.
  
  - #### 4) ease-out (Slow End): 
    - Starts at peak velocity instantly and then smoothly decelerates to a gentle stop. 
    - This is great for UI elements like dropdown menus or slide-in alerts—they pop onto the screen quickly to grab attention, then settle down smoothly.
  
  - #### 5) ease-in-out (Slow Start & Slow End): 
    - A perfect symmetry. 
    - It starts slow, accelerates through the middle, and slows back down at the very end.
- ### 4) transition-delay
-  This determines the delay at which the transition will start. 
-  In this case, the color change starts a quarter of a second after the cursor rests on the button.
  
- After this you introduce the end state-the hover state- 


---

# Performance

## 1) Stacking Context(Layering Trap)
- Think of web page as a single page of paper
- When you use properties like `transform`, `opacity`, `filter`, or `z-index`, the browser lifts that element up and places it onto its own transparent sheet of glass (a stacking context) hovering above the background.
- It will have a domino effect
- **The Setup**: when you hover over that `div`, it starts rotating, the browser isolates it onto its own layer so it can move independently
- **The Problem**: If you have lots of other elements stacked on top of or inside that same layer, the browser can't just move the div by itself. It forces the browser's rendering engine to constantly recalculate and repaint every single overlapping element on every single frame of the 2-second animation.
- **The Result**: If the browser has to redraw dozens of elements 60 times a second, the animation will stutter and look choppy.

- you should keep your animations to only affecting opacity and transform if you want absolute best performance for animations on your web page. 