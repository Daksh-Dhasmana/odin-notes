# Getter and Setter
- Getter (get): A tool that lets you read a property as a simple value while running code in the background.
- Setter (set): A tool that lets you change a property using an equals sign while running code in the background.
- eg:
- `const user = {`
`    n1: 10,`
`    n2: 0,`
`    get fullName() {`
`        return this.n1;`
`    },`
`    set fullName(val) {` `//here val is 20`
`        this.n2 = val + 2;`
`    }`
`};`
`user.fullName = 20;//Changing Property`
`console.log(user.n1);//Prints 10`
`console.log(user.n2);//Prints 22`

# Classes
- They are like blueprint for creating objects
- A Class is like a shared machine that makes many objects using one single brain; a Factory Function gives every new object its own separate brain. so Factory function will use more space and memory
 
  # Constructor
  - A constructor is a special "starter" function inside a class that automatically sets up the data for a new object the moment it is born.
  
- eg:
`class user{`
`    constructor(value){`
`        this.name=value;`
`    }`
`    out(){`
`        return this.name;`
`    }`
`}`
`let nme=new user("Hello");`
`let op=nme.out();`
`console.log(op);`

# Extends
- `extends` lets you inherit the properties/variables of another class
- eg
  `class user{`
`    constructor(value){`
`        this.name=value;`
`    }`
`    out(){`
`        return this.name;`
`    }`
`}`
`let nme=new user1("Hello");`
`let op=nme.out();`
`console.log(op);`

# Private Elements
-  Private elements get created by using a hash # prefix and cannot be legally referenced outside of the class.
-  private variables/functions cannot get inherited but an object can use them.
-  eg: #privatefunction(){}
  
# Static Elements
- Static Elements can be accessed and used by the class itself and the inherited child class.
- But the object cannot use them.
- We put `static` keyword before assigning it
- eg: `static a=10`;