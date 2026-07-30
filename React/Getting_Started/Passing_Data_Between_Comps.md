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

