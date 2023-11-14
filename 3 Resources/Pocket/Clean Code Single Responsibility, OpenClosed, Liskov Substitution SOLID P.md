---
url: https://hackernoon.com/clean-code-single-responsibility-openclosed-liskov-substitution-solid-principles-in-ts-part-4
readlater:
  id: "3963108042"
  provider: pocket
  synchtime: 1699813103223
---
![Search icon](https://hackernoon.imgix.net/search-new.png?w=19&h=19)

[![Hackernoon logo](https://hackernoon.imgix.net/hn-logo.png)![Hackernoon logo](https://hackernoon.imgix.net/hn-icon.png)](/)

[Read](/reader-boot)[Write](https://app.hackernoon.com/new)

![see notifications](https://hackernoon.imgix.net/unread-bell.png)

Notifications

see more

![](https://hackernoon.imgix.net/icons/icon-96x96.png)

[LOGIN / SIGNUP](https://app.hackernoon.com/signup)![](https://hackernoon.imgix.net/icons/SVG/awesome/Window%20Close.svg)

[![Hackernoon logo](/hn-logo.png)](/)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2725%27%20height=%2725%27/%3e)![](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![](https://hackernoon.com/brush2.png?auto=format&fit=max&w=64)

Clean Code: Single Responsibility, Open/Closed, Liskov Substitution SOLID Principles in TS [Part 4] by[@alenaananich](/u/alenaananich)

# Clean Code: Single Responsibility, Open/Closed, Liskov Substitution SOLID Principles in TS [Part 4]

[November 9th 2023](/archives/2023/11/09) New Story

---

7m

---

by @alenaananich

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2750%27%20height=%2715%27/%3e)![Open TLDR](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Open TLDR](https://hackernoon.imgix.net/tl;dr-dark.png?auto=format&fit=max&w=128)

![tldt arrow](https://hackernoon.imgix.net/arrow-dark.png)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2720%27%20height=%2720%27/%3e)![](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![](https://hackernoon.imgix.net/images/usa_flag.webp?auto=format&fit=max&w=48)

**EN**

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2725%27%20height=%2725%27/%3e)![Read on Terminal Reader](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Read on Terminal Reader](https://hackernoon.imgix.net/computer.png?auto=format&fit=max&w=64)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2725%27%20height=%2725%27/%3e)![Read this story w/o Javascript](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Read this story w/o Javascript](https://hackernoon.imgix.net/images/Lite%20Icon%20%4025px.png?auto=format&fit=max&w=64)

## Too Long; Didn't Read

In this article, we will take a look at the three first SOLID principles: The single Responsibility Principle, the Open/Closed Principle and the Liskov Substitution Principle on practical examples.

[](https://hackernoon.imgix.net/images/erom0wkF6nZC8UOvFBqlbSeNR4J2-br933z6.jpeg "Download image")

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%27800%27%20height=%27368%27/%3e)![featured image - Clean Code: Single Responsibility, Open/Closed, Liskov Substitution SOLID Principles in TS [Part 4]](https://hackernoon.imgix.net/images/erom0wkF6nZC8UOvFBqlbSeNR4J2-br933z6.jpeg?w=1200&q=75&auto=format)

![featured image - Clean Code: Single Responsibility, Open/Closed, Liskov Substitution SOLID Principles in TS [Part 4]](https://hackernoon.imgix.net/images/erom0wkF6nZC8UOvFBqlbSeNR4J2-br933z6.jpeg?w=1200&q=75&auto=format)

[programming](/c/programming) [#programming](/tagged/programming) [#typescript](/tagged/typescript)

![Alena Ananich HackerNoon profile picture](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Alena Ananich HackerNoon profile picture](https://hackernoon.imgix.net/avatars/robot-b6.png?auto=format&fit=max&w=3840)

---

### [@alenaananich](/u/alenaananich)

**Alena Ananich**

---

---

Receive Stories from @alenaananich

SUBSCRIBE SUBSCRIBE TO RECEIVE THIS WRITER'S CONTENT STRAIGHT TO YOUR INBOX!

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%2730%27%20height=%2730%27/%3e)![react to story with heart](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![react to story with heart](https://hackernoon.com/emojis/heart.png?auto=format&fit=max&w=64)

![reaction animation](https://hackernoon.com/emojis/heart.png)![reaction animation](https://hackernoon.com/emojis/heart.png)![reaction animation](https://hackernoon.com/emojis/heart.png)

[](#commentSection)

[![Alena Ananich HackerNoon profile picture](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Alena Ananich HackerNoon profile picture](https://cdn.hackernoon.com/avatars/robot-b6.png?auto=format&fit=max&w=3840)

](/u/alenaananich)

by Alena Ananich [@alenaananich](/u/alenaananich).Enjoy programming

[Read My Stories](https://hackernoon.com/u/alenaananich)

[![NEAR Protocol](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![NEAR Protocol](https://hackernoon.imgix.net/images/img-cg23atb.jpeg?auto=format&fit=max&w=3840)

](https://nearcon.app/?utm_source=hackernoon&utm_medium=category-page&utm_campaign=nearcon)

#### RELATED STORIES

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%27100%27%20height=%27100%27/%3e)![Article Thumbnail](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Article Thumbnail](https://hackernoon.imgix.net/images/erom0wkF6nZC8UOvFBqlbSeNR4J2-fya31se.jpeg?auto=format&fit=max&w=256)

**[Clean Code: Naming and Code Composition in TypeScript [Part 2]](../clean-code-naming-and-code-composition-in-typescript-part-2)**

Published at Oct 19, 2023 by [alenaananich](https://hackernoon.com/u/alenaananich) [#clean-code](/tagged/clean-code)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%27100%27%20height=%27100%27/%3e)![Article Thumbnail](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Article Thumbnail](https://hackernoon.imgix.net/images/erom0wkF6nZC8UOvFBqlbSeNR4J2-3893253.jpeg?auto=format&fit=max&w=256)

**[Clean Code: Classes and Objects in TypeScript [Part 3]](../clean-code-classes-and-objects-in-typescript-part-3)**

Published at Oct 30, 2023 by [alenaananich](https://hackernoon.com/u/alenaananich) [#cleancode](/tagged/cleancode)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%27100%27%20height=%27100%27/%3e)![Article Thumbnail](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Article Thumbnail](https://hackernoon.imgix.net/images/rIVD9uGtDyTmdfox8lpMYgJi5AZ2-gs93xx7.jpeg?auto=format&fit=max&w=256)

**[How to Migrate a React Project from JavaScript to TypeScript](../how-to-migrate-a-react-project-from-javascript-to-typescript)**

Published at Oct 19, 2023 by [leandronnz](https://hackernoon.com/u/leandronnz) [#react-projects](/tagged/react-projects)

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%27100%27%20height=%27100%27/%3e)![Article Thumbnail](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

![Article Thumbnail](https://hackernoon.imgix.net/images/Hr4zJaE09hYutGUApRLUdnqle5d2-jro3dne.jpeg?auto=format&fit=max&w=256)

**[Designing Complex Software: Tips for UX/UI Designers](../designing-complex-software-tips-for-uxui-designers)**

Published at Oct 19, 2023 by [abramova](https://hackernoon.com/u/abramova) [#ui-ux](/tagged/ui-ux)

L O A D I N G  
. . . comments & more!