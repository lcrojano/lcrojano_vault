
Before ES6 shoudl assing methods to prototype after constructior functioon

``` javascript
function Person(name){
	this.name = name;
}

Person.prototype.greet = funtion(){
	return "Hi I'm " + this.name; 
}

var person = new Person("Red");
console.log(person.greet());
```

after ES6 chaged to a syntactic sugar

``` javascript
class Person(){
	constructor(name){
		this.name = name;
	}
	greet(){
		return "Hi I'm " + this.name;
	}
}
var person = new Person("Red");
console.log(person.greet());
```