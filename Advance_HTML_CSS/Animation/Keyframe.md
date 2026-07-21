# Difference between Animation and Transition
| Transition | Animation |
| ---       | ---        |
|Transitions were designed to animate an element from one state to another. They can loop, but they weren’t designed for that. |Animations, on the other hand, were designed with the purpose of explicitly enabling loops.   
| Transitions need a trigger, such as the use of pseudo-classes like :hover or :focus, or by adding/removing a class via JavaScript| Animations, on the other hand, do not need such a trigger. Once you have your elements in place and CSS defined, an animation will start running immediately if that’s what you told it to do.
- All in all, both animations and transitions have their use, so in addition to considering the above differences you should also use your best judgment. For example, if you need to change the opacity of an element when it is active then an animation would be overkill, but if you need to carry out something more complicated, animations will provide you with the tools you need.

- ![alt text](image-1.png)
---
# Animation Properties
- Now, the animation has two parts: 1) where we define animation properties
                                    2) where we actually put it to use
## 1) Where we define animation property
-
```
#ball {
  /* order: name | duration | timing-function | delay | iteration-count | direction */
  animation: change-color 2s ease 1s infinite alternate;
}
```
- `animation-name`: 
    - Links your element to a specific @keyframes timeline rule (in this case, change-color)
- `animation-duration`: 
    - Sets the total time (e.g., 2s) it takes for the animation to complete one full cycle.
- `animation-timing-function`: 
    - The acceleration curve that dictates the speed changes throughout the timeline (e.g., ease-out, linear).
- `animation-delay`: 
    - The waiting period before the animation starts playing after the element loads or is triggered (e.g., 1s).
- `animation-iteration-count`:
    - Controls how many times the animation loops (in this case, infinite keeps it looping forever).
- `animation-direction`: 
    - Sets the playback direction (in this case, alternate makes it play forward, then backward, and repeat smoothly).

## 2) Where we actually put it to use
- Now we are gonna use `@keyframe` here
- Look at example below
```
@keyframes change-color {
  from {
    background-color: red;
  }

  to {
    background-color: green;
  }
}
```
- In above eg, we used from and to properties to change background-color of ball from red to green
- Here, it counts as 1 cycle only, so if we set `iteraton-count` to 3, it will change color from red to green 3 times
- It’s important to know that keyframes use a percentage to indicate the times for an animation to take place and that the from and to statements are actually aliases for 0% and 100%, respectively.
- So we can use `@keyframes` like this too.
- In below example, `change-color` is animation name, and it can be customised too!!
```
@keyframes change-color {
  from {
    background-color: red;
  }
  
  50% {
    transform: scale(2);
    background-color: blue;
  }

  to {
    background-color: green;
  }
}
```

- NOTE: you can also combine transition and animation too! Like This!
```
@keyframes expand {
  0%{
    transform: scaleY(0);
  }
  70%{
    transform: scaleY(1.4);
  }
  100%{
    transform: scaleY(1);
  }
}
```