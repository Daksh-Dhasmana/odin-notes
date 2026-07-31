# Introduction
- In this lesson, we will learn about React props (short for properties) and how to use props to pass data between components.

# Data Transfer in React
- In this data transfers from parent to child components via props
- Meaning it is unidirectional 
- Any changes made to this data will only affect child components using the data, and not parent or sibling components.

*NOTE: we will be using props short for properties*

# Using props in React
- Props is used to get "custom" attributes/property for an HTML elment
- eg
- **Button.jsx**
```
function Button(props){
  const butos={
    backgroundColor:props.bgcol,
    color:props.cols,
    padding: props.pads+'px'
  }
  return(
    <button style={butos} >{props.text}</button>
  );
}
export default Button
```
- **App.jsx**
```
import Button from "./Button";

function App(){
  return( 
  <>
    <Button cols="blue" bgcol="yellow" text="NAME"></Button>
    <Button pads={25} text="Roll"></Button>
    <Button text="Clas"></Button>
  </>
  );
}
export default App;
```

# Destructuring
- A very common pattern you will come across in React is prop destructuring. 
- Unpacking your props in the component parameters allows for more concise and readable code. 
- NOTE: Use this over props
- Check out prop destructuring in action in the example below.
```
function Button({ text, color, fontSize }) {
  const buttonStyle = {
    color: color,
    fontSize: fontSize + "px"
  };

  return <button style={buttonStyle}>{text}</button>;
}

export default function App() {
  return (
    <div>
      <Button text="Click Me!" color="blue" fontSize={12} />
      <Button text="Don't Click Me!" color="red" fontSize={12} />
      <Button text="Click Me!" color="blue" fontSize={20} />
    </div>
  );
}
```

# Default Props
- Default props are fallback values you give to a component's props so your code doesn't break if a prop isn't passed from the parent.
- Think of default props as a safety net: "If the parent component gives me a color, I'll use it. If not, I'll default to white."
- eg:
```
// Notice color = "black" and text = "Click Me!"
function Button({ text = "Click Me!", color = "black", padding = 10 }) {
  const buttonStyle = {
    color: color,
    padding: padding + "px"
  };

  return <button style={buttonStyle}>{text}</button>;
}
```

# Passing functions as props
- You can also pass functions as props
```
import Button from "./Button";
Button.defaultProps={
  text: "CLICK HERE",
  cls: "blue"
}
function App(){
  const sum=(num1)=>(num2)=>{
    const ans=num1+num2;
    return ans;
  }
  return( 
  <>
    <Button bgcols="black" cls="white" text={sum(1)(2)}></Button>//will show 3
    <Button ></Button>
    <Button text="Clas"></Button>
  </>
  );
}
export default App;
```