---
topic:
  - css
  - animation
tags:
  - css/animations
---
**Keyframe** in CSS defines specific points during an animation where you can set styling rules for elements, allowing precise control over animations by specifying intermediate states.

``` css
@keyframe pulse {
	0% { 
		transform: scale(1);
	}
	50%{
		transform: scale(1.1);
	}
	100%{
		transform: scale(1);
	}
	
}
```

You define each intermediate stage of the animation, form 0 to 100, in each stage you could modify specific CSS.

``` css
.element {
	width: 100px;
	height:100px;
	background-color: blue;
	animation: pulse 0.5s ease-in-out infinite;	
}
````

This keyframe animation ('pulse') is applied to an element ('.element'). It scales the element, creating a pulsing effect. The animation lasts 0.5 seconds, has an easing function ('ease-in-out'), and repeats infinitely.

