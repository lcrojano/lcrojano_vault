---
url: https://garden.bradwoods.io/notes/css/3d
readlater:
  id: "3960232713"
  provider: pocket
  synchtime: 1699293691361
---
![Wireframe of a square tunnel receding into the page](/images/popular/3DLight.svg)

# 3D in CSS

Intended Audience: Front-end developers. Anyone learning CSS.

Tended: Aug 2023

Status: [seed](/about#aboutthisgarden)

# 3D Space

The `perspective` property enables a 3D-space for child elements. Its value determines the strength of a child's z-transform effect. Large `perspective` values cause small transformations, small values cause large transformations.

## /index.css

.parent {
    perspective: 800px;
}

800px

Perspective:

Drag me

![Arrow pointing up labelled Y. Arrow pointing right labelled X. Arrow pointed towards to user labelled Z.](/images/xYZHelper.svg)

# Vanishing point

`perspectiveOrigin` defines the vanishing point. It's default value is `50% 50%`. Centered horizontally and vertically.

## /index.css

.parent {
    perspective: 800px;    perspective-origin: 50% 50%;
}

800px

Perspective:

50%s

Perspective Origin X:

50%s

Perspective Origin Y:

Drag me

![Arrow pointing up labelled Y. Arrow pointing right labelled X. Arrow pointed towards to user labelled Z.](/images/xYZHelper.svg)

# translate3d

- ▪ `translateX(...)` moves a child horizontally.
- ▪ `translateY(...)` moves a child vertically.
- ▪ `translateZ(...)` moves a child closer or further away. The strength of the effect is determined by the value of `perspective` (mentioned above).

## /index.css

.parent {
    perspective: 800px;    perspective-origin: 50% 50%;
}
.child {
    transform: translate3d(0px, 0px, -500px);
}

800px

Perspective:

50%s

Perspective Origin X:

50%s

Perspective Origin Y:

0px,s

Translate X:

0px,s

Translate Y:

-500px,s

Translate Z:

Drag me

![Arrow pointing up labelled Y. Arrow pointing right labelled X. Arrow pointed towards to user labelled Z.](/images/xYZHelper.svg)

# rotate3d

`rotate3d` rotates an element around the x, y or z axis. The first 3 arguments define the x, y and z vector. The last defines the angle.

## /index.css

.parent {
    perspective: 800px;    perspective-origin: 50% 50%;
}
.child {
    transform: translate3d(0px, 0px, -500px);    transform: rotate3d(1, 0, 0, 0deg);
}

800px

Perspective:

50%s

Perspective Origin X:

50%s

Perspective Origin Y:

0pxs,

Translate X:

0pxs,

Translate Y:

-500pxs,

Translate Z:

1,s

Rotate X:

0,s

Rotate Y:

0,s

Rotate Z:

0degs

Rotate Angle:

Drag me

x

y

z

![Arrow pointing up labelled Y. Arrow pointing right labelled X. Arrow pointed towards to user labelled Z.](/images/xYZHelper.svg)

# Use Case: Screen Realestate

When a web page transitions from being displayed on a desktop to a mobile device, there is less screen realestate to work with. When this happens, it is common to remove lower-priority elements from the UI (User Interface). Rotating elements on the y-axis provides more screen realestate to work this. This allows more of the UI to remain on the screen when transitioning to smaller devices.

Drag the bottom-right corner of the list below. As the width gets smaller, the `ul` rotates on the y-axis. Providing more space for content to the right of the list.

- index.html
- index.css
- index.js
- Show All Code

## localhost:3000

const ul = document.querySelector('ul')
// Increase to get more of an effect
const strength = 0.1
function rotateUl() {
   const windowWidth = window.innerWidth   const ulWidth = ul.getBoundingClientRect().width   const rotate = Math.max((windowWidth - ulWidth) * strength, 0)
   ul.style.transform = `perspective(400px) rotateY(${rotate}deg)`
}
function onMouseDown() {
   window.addEventListener("mousemove", rotateUl)
}
function onMouseUp() {
   window.removeEventListener("mousemove", rotateUl)
}
ul.onmousedown = onMouseDown
ul.onmouseup = onMouseUp

![Images of elevator floor numbers](/_next/image?url=%2Fimages%2FdavidCarsonElevator.webp&w=640&q=75)

This does come with a cost. The greater the rotation, the more readability is lost. However, we don't always need 100% readability. Graphic designer [David Carson](https://www.masterclass.com/classes/david-carson-teaches-graphic-design) once designed numbers for the floors of a hotel. They would be the first thing a guest sees when stepping off the elevator. He created images that are a combination of the number and the word of the number (with missing letters) in unusual arrangements. His design isn't readable, but is understandable.

# Use Case: Different Perspective

Sometimes a thing can be better communicated when shown from multiple perspectives. Below is an wireframe of a web page I used in a presentation. I needed to communicate there are 3 elements in the top-right corner, stacked on top of 1 another. By translating and rotating this wireframe in a 3D-space, I can show it from a 2nd perspective.

- index.html
- index.css
- index.js
- Show All Code

## localhost:3000

#parent {
   perspective: 1000px;
}
#child {
   width: 100%;   height: 100%;
   position: relative;
   perspective: 1000px;   transform-style: preserve-3d;   transition: transform var(--time);
   border: 1px solid var(--black);
}
#parent[data-rotate=true] #child {
   transform: translate3d(0, 0, -200px) rotate3d(0.1, -0.1, 0.1, 86deg);
}
.grandChild {
   transition: transform var(--time);
}
#parent[data-rotate=true] .grandChild {
   transition-delay: var(--time);
}
#parent[data-rotate=true] .grandChild:nth-child(2) {
   transform: translate3d(0, 0, 20px);
}
#parent[data-rotate=true] .grandChild:nth-child(3) {
   transform: translate3d(0, 0, 40px);
}

Above, the `transform-style: preserve-3d` is set on the `#child` element. This makes children of a transformed element exist in their own 3D-space. Without it, `.grandChild` elements will be flattened to the plane of the `#child` element. It you remove that line, you will see `.grandChild` elements don't translate.

# Other Use Cases

- ▪ When explaining a process, to help the user [maintain context](https://pomb.us/build-your-own-react/) when moving from 1 step to the next.
- ▪ A different approach to a [presentation slide deck](https://impress.js.org/).
- ▪ To communicate [complex architecture](https://c4model.com/) from big picture to low-level detail without overwhelming the user. Through the use of zoom to show / hide information.
- ▪ [Flair](https://leebyron.com/)

# Support Me

![The Weighted Companion Cube from Aperture](/_next/image?url=%2Fimages%2FcompanionCube.webp&w=640&q=75)

- [
    
    Patreon
    
    ](https://www.patreon.com/bradwoods)
- [
    
    Buy me a coffee
    
    ](https://ko-fi.com/bradwoods)
- [
    
    Follow
    
    ](https://twitter.com/bradwoodsio)

# Where to Next?

[Notes](/)

CSS

YOU ARE HERE

3D

[Alignment Click Target](/notes/css/alignment-click-target)

[Blend Modes](/notes/css/blend-modes)

[Box Sizing](/notes/css/box-sizing)

[Floating Image](/notes/css/floating-image)

[Layout Component](/notes/css/layout-component)

[Reset](/notes/css/reset)

[Typography Setup](/notes/css/typography-setup)

![A sci-fi robot taxi driver with no lower body](/_next/image?url=%2Fimages%2FjohnnyCab.webp&w=640&q=75)

![](/_next/image?url=%2Fimages%2FjohnnyCabLights1.webp&w=640&q=75)

![](/_next/image?url=%2Fimages%2FjohnnyCabLights2.webp&w=640&q=75)