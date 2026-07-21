# Transform
- The transform CSS property lets you rotate, scale, skew, or translate an element. It modifies the coordinate space of the CSS visual formatting model.
- It is a powerful tool to change appearance.
- They are commonly used for animated effects.

---

## 2D Transformations
- For 2D transformation, we use: rotate, scale, skew, translate
  
### 1) Rotate
- This is the transform function value to rotate an element on a 2D plane
- Syntax:
  ```
  .element {
  transform: rotate();
  }
  ```
- Here we can put any sort of degree, like radians, degree, etc.
- eg:
  ```
  .rotate-by-deg {
  transform: rotate(45deg);
  }
  ```
  ```
  .rotate-by-rad {
  transform: rotate(-1rad);
  }
  ```

### 2) Scale
- These are the transform function values to scale an element on a 2D plane:
```
 .element {
  transform: scaleX();
  transform: scaleY();
  transform: scale();
}
```

### 3) Skew
- These are the transform function values to skew an element on a 2D plane:

- Skew refers to the visual distortion that happens when you tilt an object along an axis. 
- Instead of rotating the whole shape, it pushes one side of the object while keeping the base anchored, shifting the internal angles.
- Syntax:
```
.element {
  transform: skewX();
  transform: skewY();
  transform: skew();
}
```
### 4) Translate
- These are the transform function values to translate an element on a 2D plane:
- translate means to move an object from one position to another without rotating it, resizing it, or distorting its shape
- Syntax: 
```
.element {
  transform: translateX();
  transform: translateY();
  transform: translate();
}
```
### Chaining Transforms
```
.image{
    transform: scale(110%) rotate(90deg);
}
```
---
## 3D Transformation
- The rotate, scale, and translate transform functions aren’t limited to just 2D planes. They also work for 3D planes as well! 
- However, to perceive a 3D effect on some of these function values, `perspective()` is required.
- eg: 
```
.image{
    transform: perspective();
}
```
### 1) Rotate
- Now we can also rotate in 3D
```
.element {
  transform: rotateX();
  transform: rotateY();
  transform: rotateZ();
  transform: rotate3d();
}
```

### 2) Scale
- We can scale in 3D space
```
.element {
  transform: scaleZ(z); //Scales it along z-axis
  transform: scale3d(x,y,z);
}
```

### 3) Translate
- These are the additional transform function values to translate an element in a 3D space:
- `translateZ `doesn’t do much without `perspective`. Instead, perspective and `translateZ` work together to create the illusion of 3-dimensional distance from the rendered object, as shown in the example below.
- Syntax:
```
.element {
  transform: translateZ();
  transform: translate3d();
}
```
- eg:
```
.translate30 {
  transform: perspective(100px) translateZ(30px);
}
```
---
## Transform-origin Property
- The `transform-origin` property allows you to change the position of transformed elements.
- Syntax
`transform-origin: x-axis y-axis z-axis;`
- Default value is 50% 50% 0.

### Property-values
- ![Not_loading](image.png)