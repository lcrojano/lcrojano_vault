---
Type:
  - Note
tags:
  - javascript/best-practices
Status: In-Progress
---
JavaScript Scope is determined at compiling time, this makes javascript a Static Scope, it means that variables are determined at compilation time and not at execution time.
also known as [[lexical scopelexical scope]]

``` javascript
const number = 10;  
 function printNumber() {  

console.log(number);  
}  
  
function app() {  
const number = 5;  
 printNumber();  
}  
  
 app(); //10
```

this means that  scope is determined before execution of the code, at compiling time. If JavaScript were dynamic, the scope would be determined at execution time.