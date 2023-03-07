## The For Of Loop
[[JS]]
The JavaScript `for of` statement loops through the values of an iterable object.

It lets you loop over iterable data structures such as Arrays, Strings, Maps, NodeLists, and more:

### Syntax

for (variable of [[Iterables]] ) {  
  // _code block to be executed_  
}  

**variable** - For every iteration the value of the next property is assigned to the variable. _Variable_ can be declared with `const`, `let`, or `var`.

**iterable** - An object that has iterable proper

## Looping over an Array

### Example

const cars = ["BMW", "Volvo", "Mini"];  
  
let text = "";  
for (let x of cars) {  
  text += x;  
}  

---

## Looping over a String

### Example

let language = "JavaScript";  
  
let text = "";  
for (let x of language) {  
text += x;  
}