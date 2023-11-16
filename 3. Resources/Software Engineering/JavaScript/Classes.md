Before ES6
no class word exist. It was a common function, but assigning a value to this (prototype)
``` javascript
function Car(name){
	this.name = name;
}

var car = new Car("Tesla");
```

After ES6
class reserved word was introduced as syntactic sugar
``` javascript
class Car{
	constructor(name){
		this.name = name;
	}
}

const car = new Car("Tesla");
```

