---
url: https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0
readlater:
  id: "3954265112"
  provider: pocket
  synchtime: 1699293687436
---
[![Cover image for Unlocking JavaScript Design Patterns: Mastering Singleton for Ultimate Code Efficiency](https://res.cloudinary.com/practicaldev/image/fetch/s--hJiNrtd2--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vb4icr9l8u82f2o0yeqr.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--hJiNrtd2--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vb4icr9l8u82f2o0yeqr.png)

[![Nicolas B.](https://res.cloudinary.com/practicaldev/image/fetch/s--T4_VYnZy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1129301/e0beaa0a-407f-4ae9-b04f-6b3a4f61f3b0.jpeg)](/brdnicolas)

[Nicolas B.](/brdnicolas)

Posted on Oct 23 • Originally published at [brdnicolas.com](https://brdnicolas.com/articles/js-singleton-pattern)

   ![](https://dev.to/assets/sparkle-heart-5f9bee3767e18deb1bb725290cb151c25234768a0e9a2bd39370c382d02920cf.svg)  ![](https://dev.to/assets/multi-unicorn-b44d6f8c23cdd00964192bedc38af3e82463978aa611b4365bd33a0f1f4f3e97.svg)  ![](https://dev.to/assets/exploding-head-daceb38d627e6ae9b730f36a1e390fca556a4289d5a41abb2c35068ad3e2c4b5.svg)  ![](https://dev.to/assets/raised-hands-74b2099fd66a39f2d7eed9305ee0f4553df0eb7b4f11b01b6b1b499973048fe5.svg) ![](https://dev.to/assets/fire-f60e7a582391810302117f987b22a8ef04a2fe0df7e3258a5f49332df1cec71e.svg)

# Unlocking JavaScript Design Patterns: Mastering Singleton for Ultimate Code Efficiency

[#javascript](/t/javascript) [#designpatterns](/t/designpatterns) [#programming](/t/programming) [#tutorial](/t/tutorial)

## [patterns (2 Part Series)](/brdnicolas/series/25119)

[1 Unlocking JavaScript Design Patterns: Mastering Singleton for Ultimate Code Efficiency](/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0 "Published Oct 23") [2 Mastering Real-Time Magic: The Observer Pattern](/brdnicolas/mastering-real-time-magic-the-observer-pattern-1l0k "Published Oct 30")

In the world of JavaScript, design patterns are your secret weapon to crafting efficient, organized, and maintainable code. Among these patterns, the Singleton pattern stands out as a versatile powerhouse, **enabling you to ensure a single instance of a class throughout your application**. Let's see how it works !

---

## [](#the-singleton-pattern-demystified)The Singleton Pattern Demystified

The Singleton pattern, at its core, **guarantees that a class has only one instance** and **provides a global point of access to that instance**. This means that no matter how many times you request an instance of the class, you will a*_lways get the same one__. Singleton is particularly **useful when you need to manage shared resources or control access to a single point_*, such as a configuration manager, database connection, or, in our case, a logging system.

---

## [](#the-logger-example)The Logger Example

### [](#setting-up-the-logger)Setting Up the Logger

Imagine you're building a JavaScript application that consists of multiple modules and files. **Debugging and tracking issues across the application can become challenging without a unified logging system**. This is where the Singleton pattern comes to the rescue.

Let's create a simple logger that will maintain a single log throughout the application. Here's our `logger.js` file:  

```
class Logger {
  constructor() {
    this.logs = [];
  }

  log(message) {
    this.logs.push(message);
  }

  showLogs() {
    console.log(this.logs);
  }

  static getInstance() {
    if (!this.instance) {
      this.instance = new Logger();
    }
    return this.instance;
  }
}

export default Logger;
```

 

In this implementation, we've defined a `Logger` class that allows logging messages and displaying them. **The `getInstance` static method ensures that only one instance of the `Logger` class exists throughout your application.**

--

### [](#use-the-singleton-logger)Use the Singleton Logger

Now, let's see how we can utilize the Singleton logger in different parts of our application.

**app.js (Usage in One File)**  

```
import Logger from './logger.js';

const loggerInstance1 = Logger.getInstance();
loggerInstance1.log('Log message 1');
loggerInstance1.log('Log message 2');

loggerInstance1.showLogs();
```

 

In `app.js`, we import the Logger instance, **create** a `loggerInstance1`, and use it to log messages. The beauty of the Singleton pattern is that **we are always working with the same instance**, ensuring that **all logs are stored in one centralized location**.

**anotherFile.js (Usage in Another File)**  

```
import Logger from './logger.js';

const loggerInstance2 = Logger.getInstance();
loggerInstance2.log('Log message from another file');

loggerInstance2.showLogs();
```

 

In `anotherFile.js`, we again **import the same `Logger` instance** and use `loggerInstance2`. **Despite being in a different file, loggerInstance2 is essentially the same instance as `loggerInstance1`**. This means that all logs from both files are accumulated in the same log array, giving you a comprehensive overview of your application's behavior.

---

## [](#benefits-of-the-singleton-logger)Benefits of the Singleton Logger

Implementing the Singleton pattern for a logger in your JavaScript application offers several benefits:

1 - **Centralized Logging**: All log messages are **collected in one place**, making it easier to trace application behavior and debug issues.

2 - **Consistency**: You can be confident that you're working with **the same logger instance** throughout your application, ensuring **data integrity**.

3 - **Easy Integration**: The Singleton logger seamlessly integrates into different parts of your code, enhancing overall **code efficiency**.

---

## [](#conclusion)Conclusion

The Singleton pattern is a powerful tool in JavaScript, providing **a straightforward way to manage shared resources and maintain a single point of control in your application**. As demonstrated through our logger example, it ensures that you have one consistent logger instance, simplifying debugging and enhancing code efficiency.

By mastering the Singleton pattern and using it wisely, you can **unlock the full potential of your JavaScript applications**, making them more organized, maintainable, and efficient.

[My Linkedin](https://linkedin.com/in/brdnicolas)  
[My X](https://x.com/_brdnicolas)  
[My portfolio](https://brdnicolas.com)

## [patterns (2 Part Series)](/brdnicolas/series/25119)

[1 Unlocking JavaScript Design Patterns: Mastering Singleton for Ultimate Code Efficiency](/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0 "Published Oct 23") [2 Mastering Real-Time Magic: The Observer Pattern](/brdnicolas/mastering-real-time-magic-the-observer-pattern-1l0k "Published Oct 30")

## Top comments (13)

### Sort discussion:

- [
    
     Top
    
    Most upvoted and relevant comments will be first
    
    ](/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0?comments_sort=top#toggle-comments-sort-dropdown)
- [
    
    Latest
    
    Most recent comments will be first
    
    ](/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0?comments_sort=latest#toggle-comments-sort-dropdown)
- [
    
    Oldest
    
    The oldest comments will be first
    
    ](/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0?comments_sort=oldest#toggle-comments-sort-dropdown)

Subscribe

    ![pic](https://res.cloudinary.com/practicaldev/image/fetch/s--V3djhsWJ--/c_limit,f_auto,fl_progressive,q_auto,w_256/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8j7kvp660rqzt99zui8e.png)

Personal Trusted User

[Create template](/settings/response-templates)

Templates let you quickly answer FAQs or store snippets for re-use.

Submit Preview [Dismiss](/404.html)

 

 

[![devdufutur profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--GL-1herd--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/202313/cda6c9ab-a361-45d0-ad1c-acd035022a2e.jpg)](https://dev.to/devdufutur)

[Rudy Nappée](https://dev.to/devdufutur)

Rudy Nappée

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--XmgfCyiU--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/202313/cda6c9ab-a361-45d0-ad1c-acd035022a2e.jpg)Rudy Nappée](/devdufutur)

Follow

French freelance dev

- Location
    
    France
    
- Work
    
    Lead dev at Niort
    
- Joined
    
    Jul 27, 2019
    

• [Oct 23 • Edited on Oct 23 • Edited](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8m6)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8m6)

- Hide

Actually in JS, any ES module is a singleton ! No need for getInstance() or any other fancy OOP stuff 😅

14 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8m6)

 

 

[![syeo66 profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--mTdJeXgS--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/719942/708432c9-3b6a-4dbb-afa3-3def288ffb53.jpeg)](https://dev.to/syeo66)

[Red Ochsenbein (he/him)](https://dev.to/syeo66)

Red Ochsenbein (he/him)

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--j6-3Gewm--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/719942/708432c9-3b6a-4dbb-afa3-3def288ffb53.jpeg)Red Ochsenbein (he/him)](/syeo66)

Follow

A senior at work, a beginner at heart.

- Location
    
    Burgdorf, Switzerland
    
- Pronouns
    
    he/him
    
- Joined
    
    Oct 5, 2021
    

• [Oct 23](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8ma)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8ma)

- Hide

Was about to say the same thing.

6 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8ma)

 

 

[![zeroevidence profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--b2tTlolF--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1192884/b85e34d4-59a3-4109-9936-48a8f776b80d.jpeg)](https://dev.to/zeroevidence)

[Dale Moore](https://dev.to/zeroevidence)

Dale Moore

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--WLfotMdZ--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1192884/b85e34d4-59a3-4109-9936-48a8f776b80d.jpeg)Dale Moore](/zeroevidence)

Follow

- Joined
    
    Oct 24, 2023
    

• [Oct 24](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a977)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a977)

- Hide

You beat me to it!

3 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a977)

 

 

[![teamradhq profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--l_Zp_oT7--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/56237/3d77816c-3b0c-4d6f-b96e-c340ddecf257.jpeg)](https://dev.to/teamradhq)

[teamradhq](https://dev.to/teamradhq)

teamradhq

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--sqxla2cB--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/56237/3d77816c-3b0c-4d6f-b96e-c340ddecf257.jpeg)teamradhq](/teamradhq)

Follow

- Location
    
    Melbourne, Australia
    
- Joined
    
    Feb 2, 2018
    

• [Oct 25](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9ij)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9ij)

- Hide

To expand on what others are saying regarding ES modules being singletons: what this means is that every module you load in your program is only evaluated once.

So, while you can import a module multiple times, any code that's executed within its immediate scope only runs on the first import.

In your example, the way you would implement `Logger` as singleton is to just export an instance of the class:  

```
// logger.mjs
console.log('Logger module loaded');

class Logger {
  constructor() {
    this.logs = [];
  }

  log(message) {
    this.logs.push(message);
  }

  showLogs() {
    console.log(this.logs);
  }
}

export default new Logger();
```

 

This guarantees that will only ever be one instance of `Logger` per process.

Consider this application structure:  

```
// index.js
import logger from './logger.mjs';
import './module-a.mjs';
import './module-b.mjs';

console.log('Index loaded');
logger.log('Index:1');
logger.log('Index:2');
logger.showLogs();
```

 

```
// module-a.mjs
import logger from './logger.mjs';

console.log('Module A loaded');
logger.log('Module A:1');
logger.log('Module A:2');
```

 

```
import logger from './logger.mjs';

console.log('Module B loaded');
logger.log('Module B:3');
logger.log('Module B:4');
```

 

When we run `index.mjs` this is the output:  

```
#$ node ./index.js
Logger module loaded
Module A loaded
Module B loaded
Index loaded
[
  'Module A:1',
  'Module A:2',
  'Module B:3',
  'Module B:4',
  'Index:1',
  'Index:2'
]
```

 

As you can see, all logs are sent to the same instance and modules are only evaluated the first time they're imported.

8 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a9ij)

 

 

[![brdnicolas profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--T4_VYnZy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1129301/e0beaa0a-407f-4ae9-b04f-6b3a4f61f3b0.jpeg)](https://dev.to/brdnicolas)

[Nicolas B.](https://dev.to/brdnicolas)

Nicolas B.

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--d3Lc_hHU--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1129301/e0beaa0a-407f-4ae9-b04f-6b3a4f61f3b0.jpeg)Nicolas B.](/brdnicolas)

Follow

A simple fullstack developer

- Email
    
    [contact@brdnicolas.com](mailto:contact@brdnicolas.com)
    
- Location
    
    Paris
    
- Joined
    
    Jul 30, 2023
    

• [Oct 25](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9k4)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9k4)

- Hide

Thank you for your very good explanation!

1 like Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a9k4)

 

 

[![grunk profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--HJicQAA_--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/890877/76ebd698-87ec-40e2-825d-84e4f0ea78de.jpg)](https://dev.to/grunk)

[Olivier](https://dev.to/grunk)

Olivier

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--3-f_r7S_--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/890877/76ebd698-87ec-40e2-825d-84e4f0ea78de.jpg)Olivier](/grunk)

Follow

French full stack lead dev. Playing with stuff like PHP, emberjs, C++, Java, ...

- Work
    
    Lead Dev
    
- Joined
    
    Jul 12, 2022
    

• [Oct 23 • Edited on Oct 23 • Edited](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8d5)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8d5)

- Hide

In your exemple nothing prevent 2 instance of the logger class which is the heart of the singleton "pattern".  
Moreover your variable holding the instance reference is public hence the risk of letting the anyone resetting it to null.

A more secure approch could be :  

```
class Logger {
  static #instance = null
  constructor() {
    if (Logger.#instance) {
      throw new Error("Singleton is limited to one instance. Use getInstance instead")
    }
    this.logs = [];
  }

  log(message) {
    this.logs.push(message);
  }

  showLogs() {
    console.log(this.logs);
  }

  static getInstance() {
    if (!Logger.#instance) {
      Logger.#instance = new Logger();
    }
    return Logger.#instance;
  }
}
```

 

Instance is private to the class , constructor will throw an error if an other instance exists

6 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8d5)

 

 

[![brdnicolas profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--T4_VYnZy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1129301/e0beaa0a-407f-4ae9-b04f-6b3a4f61f3b0.jpeg)](https://dev.to/brdnicolas)

[Nicolas B.](https://dev.to/brdnicolas)

Nicolas B.

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--d3Lc_hHU--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1129301/e0beaa0a-407f-4ae9-b04f-6b3a4f61f3b0.jpeg)Nicolas B.](/brdnicolas)

Follow

A simple fullstack developer

- Email
    
    [contact@brdnicolas.com](mailto:contact@brdnicolas.com)
    
- Location
    
    Paris
    
- Joined
    
    Jul 30, 2023
    

• [Oct 23](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8fg)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8fg)

- Hide

Very interesting approach, thank's for your feedback :)

1 like Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8fg)

 

 

[![dsaga profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--N531TqKy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1178483/2698ca39-cdbe-445f-b181-f509b8772e60.jpeg)](https://dev.to/dsaga)

[Dusan Petkovic](https://dev.to/dsaga)

Dusan Petkovic

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--K5n0YO9a--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1178483/2698ca39-cdbe-445f-b181-f509b8772e60.jpeg)Dusan Petkovic](/dsaga)

Follow

Front-end software engineer with full-stack experience eager to learn new things to find material for my blog :/

- Location
    
    Paracin, Serbia
    
- Pronouns
    
    he/him
    
- Joined
    
    Oct 6, 2023
    

• [Oct 24](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a92g)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a92g)

- Hide

If es modules are used, we wouldn't even need to worry about multiple instances being created, we could just:

export const logger = new Logger();

Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a92g)

 

 

[![marcus_hoang profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--L6Y_gqlg--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/293591/7498df2d-7bca-4bf5-a52e-30375ffe293b.jpeg)](https://dev.to/marcus_hoang)

[Khánh Hoàng (Marcus)](https://dev.to/marcus_hoang)

Khánh Hoàng (Marcus)

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--BOGwArUd--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/293591/7498df2d-7bca-4bf5-a52e-30375ffe293b.jpeg)Khánh Hoàng (Marcus)](/marcus_hoang)

Follow

- Location
    
    Vietnam
    
- Work
    
    JS Developer at Danang
    
- Joined
    
    Dec 16, 2019
    

• [Oct 23](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8gd)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8gd)

- Hide

I agree with [@grunk](https://dev.to/grunk) comment, and we should make the `access modifier` of `constructor` is private to prevent new class  

```
class Logger {
  static #instance = null
  private constructor() {
    if (Logger.#instance) {
      throw new Error("Singleton is limited to one instance. Use getInstance instead")
    }
    this.logs = [];
  }

  log(message) {
    this.logs.push(message);
  }

  showLogs() {
    console.log(this.logs);
  }

  static getInstance() {
    if (!Logger.#instance) {
      Logger.#instance = new Logger();
    }
    return Logger.#instance;
  }
}
```

 

3 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8gd)

 

 

[![grunk profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--HJicQAA_--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/890877/76ebd698-87ec-40e2-825d-84e4f0ea78de.jpg)](https://dev.to/grunk)

[Olivier](https://dev.to/grunk)

Olivier

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--3-f_r7S_--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/890877/76ebd698-87ec-40e2-825d-84e4f0ea78de.jpg)Olivier](/grunk)

Follow

French full stack lead dev. Playing with stuff like PHP, emberjs, C++, Java, ...

- Work
    
    Lead Dev
    
- Joined
    
    Jul 12, 2022
    

• [Oct 23](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8j8)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8j8)

- Hide

Unfortunately you can't in JS 😉

2 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8j8)

 

 

[![dsaga profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--N531TqKy--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1178483/2698ca39-cdbe-445f-b181-f509b8772e60.jpeg)](https://dev.to/dsaga)

[Dusan Petkovic](https://dev.to/dsaga)

Dusan Petkovic

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--K5n0YO9a--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1178483/2698ca39-cdbe-445f-b181-f509b8772e60.jpeg)Dusan Petkovic](/dsaga)

Follow

Front-end software engineer with full-stack experience eager to learn new things to find material for my blog :/

- Location
    
    Paracin, Serbia
    
- Pronouns
    
    he/him
    
- Joined
    
    Oct 6, 2023
    

• [Oct 24](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a92h)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a92h)

- Hide

If there are multiple methods that we can execute as part of the logging mechanism then probably a class approach like in the example would be a good solution vs just es modules, that way its more explicit

2 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a92h)

 

 

[![justthev profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--Zja7cxXd--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1175172/43507a93-5e3c-44dd-81e1-c4184e7b9379.png)](https://dev.to/justthev)

[V](https://dev.to/justthev)

V

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--Ff1crulS--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1175172/43507a93-5e3c-44dd-81e1-c4184e7b9379.png)V](/justthev)

Follow

- Location
    
    Paris
    
- Education
    
    Self taught a lot with books and MooC, then joined ETNA and bought lot more books
    
- Work
    
    Software Engineer @ Wecasa
    
- Joined
    
    Oct 2, 2023
    

• [Oct 23](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8bd)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a8bd)

- Hide

Very interesting thanks!

2 likes Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a8bd)

 

 

[![shinigami92 profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--YRfitWQV--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/358199/74883e8e-d38e-45e0-8961-6c08af3e2ce2.jpeg)](https://dev.to/shinigami92)

[Shinigami](https://dev.to/shinigami92)

Shinigami

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--KZJA1Ywg--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/358199/74883e8e-d38e-45e0-8961-6c08af3e2ce2.jpeg)Shinigami](/shinigami92)

Follow

Currently mainly frontend developer who loves Material Design and Vue + Vuetify Also a passionate TypeScript enthusiast

- Location
    
    Hamburg
    
- Work
    
    Frontend Developer at adSoul GmbH
    
- Joined
    
    Mar 31, 2020
    

• [Oct 25](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9kg)

- [Copy link](https://dev.to/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0#comment-2a9kg)

- Hide

I appreciate all the ESM comments, but I have a usecase where I create named logger instances.  
So I call `const logger = loggerFactory('MyService');` and behind that I have a `Map<string, Logger>`

1 like Like [ Reply](#/brdnicolas/unlocking-javascript-design-patterns-mastering-singleton-for-ultimate-code-efficiency-4ne0/comments/new/2a9kg)

[Code of Conduct](/code-of-conduct) • [Report abuse](/report-abuse)

Are you sure you want to hide this comment? It will become hidden in your post, but will still be visible via the comment's [permalink](#).

Hide child comments as well

Confirm

For further actions, you may consider blocking this person and/or [reporting abuse](/report-abuse)