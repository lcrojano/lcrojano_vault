Before ES6 you needed to 
- create constructor function
- assign a new object based on father to the constructor prototype.
- assign new functions to prototype. 

``` javascript
function Programmer(name){
	this.name = name
}

Programmer.prototype = Object.create(Person.prototype);

Programmer.prototype.writeCode = function(){
	return "Ok writing best code."
}

var person = new Programmer("Jhon")
console.log(person.greet());
console.log(person.writeCode();
```

After ES6
notice the use of super and new extends word.
``` javascript
class Programmer extends Person {
	constructor(name){
		super(name);
	}
	writeCode(){
		return "Ok writing best code."
	}
}
const person = new Programmer("Jhon")
console.log(person.greet());
console.log(person.writeCode();
```