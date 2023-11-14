---
topic:
  - javascript
  - animation
---
Create animations for HTML elements using JavaScript by altering the Document Object Model ([[DOM]]).

``` javascript
let isAnimating = false;
const box = document.getElementById("box");
box.addEventListener("click", () => {
	if(!isAnimating){
		isAnimating = true;
		box.style.transform = 'translateX(200)';
		setTimeout(() =>{
			box.style.transform = 'translateX(0)';
			isAnimating = false;
		}, 
		1000);
	}
});
```

The code demonstrates a simple horizontal animation on the "box" element upon clicking, showcasing how JavaScript can manipulate CSS properties to achieve [[CSS animation]].


