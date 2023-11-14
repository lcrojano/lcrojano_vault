---
url: https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410
readlater:
  synchtime: 1699558986818
---
[![Cover image for A guide to Auth & Access Control in web apps 🔐](https://res.cloudinary.com/practicaldev/image/fetch/s--H5VOEGdv--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u32isresapnjcm31t2eu.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--H5VOEGdv--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u32isresapnjcm31t2eu.png)

[![Wasp profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--BUQWFMFn--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/organization/profile_image/3369/c86918f8-76a9-4b01-accf-cc257f9ee56f.png)](/wasp) [![vincanger](https://res.cloudinary.com/practicaldev/image/fetch/s--fDSYGiN---/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/982343/99b7a039-13b3-4eb5-820b-da74b180ddf6.jpeg)](/vincanger)

[vincanger](/vincanger) for [Wasp](/wasp)

Posted on Nov 7 • Originally published at [wasp-lang.dev](https://wasp-lang.dev/blog/2022/11/29/permissions-in-web-apps)

   ![](https://dev.to/assets/sparkle-heart-5f9bee3767e18deb1bb725290cb151c25234768a0e9a2bd39370c382d02920cf.svg)  ![](https://dev.to/assets/multi-unicorn-b44d6f8c23cdd00964192bedc38af3e82463978aa611b4365bd33a0f1f4f3e97.svg)  ![](https://dev.to/assets/exploding-head-daceb38d627e6ae9b730f36a1e390fca556a4289d5a41abb2c35068ad3e2c4b5.svg)  ![](https://dev.to/assets/raised-hands-74b2099fd66a39f2d7eed9305ee0f4553df0eb7b4f11b01b6b1b499973048fe5.svg) ![](https://dev.to/assets/fire-f60e7a582391810302117f987b22a8ef04a2fe0df7e3258a5f49332df1cec71e.svg)

# A guide to Auth & Access Control in web apps 🔐

[#webdev](/t/webdev) [#authentication](/t/authentication) [#authjs](/t/authjs) [#permissions](/t/permissions)

At Wasp, we are working on a config language / DSL for building web apps that integrates with React & Node.js.  
  
This requires us to deeply understand different parts of what constitutes a web app, in order to be able to model them in our DSL.

Recently our focus was on access control, and I decided to capture the learnings in this blog post, to help others quickly get up to speed on how to do access control in web apps.

So, if you are new to access control in web apps, or have been doing it for some time but want to get a better idea of standard practices, read along!

#### [](#quick-overview-of-what-this-blog-post-covers)Quick overview of what this blog post covers:

1. Permissions, yay! Wait, what are they though? (quick overview of basic terms)
2. Where do we check permissions in a web app: frontend vs backend vs db
3. Common approaches (RBAC, ABAC, …)
4. OWASP recommendations
5. Implementing access control in practice
6. Summary ([TLDR](#summary-tldr))

## [](#1-permissions-yay-wait-what-are-they-though)1. Permissions, yay! Wait, what are they though?

Unless your web app is mostly about static content or is a form of art, it will likely have a notion of users and user accounts.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--kEWFk-US--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/f6ykw5lgwb8g2dfz0gx9.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--kEWFk-US--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/f6ykw5lgwb8g2dfz0gx9.png)

In such a case, you will need to know which user has permissions to do what -> who can access which resources, and who can execute which operations.

Some common examples of permissions in action:

1. User can access only their own user account.
2. If the user is an admin, they can ban other users’ accounts.
3. User can read other users’ articles, but can't modify them.
4. The title and description of the article behind the paywall are publicly accessible, but the content is not.
5. User can send an email invitation to up to 10 future users per day.

### [](#aha-you-mean-access-control-sorry-authorization-hmm-authentication)Aha, you mean access control! Sorry, authorization! Hmm, authentication?

There are different terms out there (authentication, authorization, access control, permissions) that are often confused for each other, so let's quickly clarify what each one of them stands for.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--OL4eAllV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3vl9j9yds8h78umwogva.jpg)](https://res.cloudinary.com/practicaldev/image/fetch/s--OL4eAllV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3vl9j9yds8h78umwogva.jpg)

### [](#1-authentication-or-as-the-cool-kids-would-say-authn)1) Authentication (or as the cool kids would say: authN)

Act of verifying the user's identity.  
  
Answers the question "**Who are they?**"

> A: Knock Knock  
>   
> B: Who is it?  
>   
> A: User!  
>   
> B: User who?  
>   
> A: Authorization: Basic myusername:mypassword
> 
> -> yes, you noticed correctly, this is an example of common authentication method but HTTP header is called "Authorization"! Weird! But it all makes sense if you squint hard enough: ([https://stackoverflow.com/questions/30062024/why-is-the-http-header-for-authentication-called-authorization](https://stackoverflow.com/questions/30062024/why-is-the-http-header-for-authentication-called-authorization)).

### [](#2-authorization-or-as-the-cool-kids-would-say-authz)2) Authorization (or as the cool kids would say: authZ)

Process of determining access rights that user has.  
  
Answers the question "**Are they allowed to do this?**"

Normally you will want the user to be authenticated at this point already, so you have information about them based on which you will decide if they are allowed to do something.

### [](#3-access-control)3) Access Control

A higher-level term (compared to authN and authZ) that encompasses the whole process of ensuring that only allowed parties can access specific resources (controlling access to resources -> access control).

Often consists of authentication and/or authorization as its steps.

Also often used in the wild interchangeably with just "authorization".  
Reference (OWASP): [https://www.cgisecurity.com/owasp/html/ch08.html](https://www.cgisecurity.com/owasp/html/ch08.html)

### [](#4-permissions)4) Permission(s)

A more general/informal term, closest in meaning to "authorization" when used in the context of computer science.

**Permission** to **access** a **resource** is called **authorization**.

### [](#all-together)All together

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--YyoQGgLU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b2vwdu4zqhddc4ivc39r.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--YyoQGgLU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b2vwdu4zqhddc4ivc39r.png)

Let’s see these terms used in a sentence by observing the following imagined pull request (PR):

> Title: Added **access control** to the app.
> 
> Description:  
>   
> I implemented a way for users to **authenticate** via email and password or via Google.  
>   
> On the server-side, I added **permission checks** to most of our REST API handlers, to ensure an **authenticated** user is **authorized** to execute them.  
>   
> If the user is not **authorized**, we throw an HTTP error 403.  
>   
> There are also some public parts of REST API where the user doesn’t have to be **authenticated**.

## [](#finding-this-article-useful)Finding this article useful?

We're working hard at [Wasp](https://wasp-lang.dev) to create content like this, not to mention building a modern, open-source React/NodeJS framework that allows you to "roll-your-own" auth in just a few lines of code.

If you want to see more content like this, you can help us out really easily by [giving us a star on GitHub!](https://www.github.com/wasp-lang/wasp).

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--xlfkBbiL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qgbmn45pia04bxt6zf83.gif)](https://res.cloudinary.com/practicaldev/image/fetch/s--xlfkBbiL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qgbmn45pia04bxt6zf83.gif)

[⭐️ Star Wasp on GitHub 🙏](https://www.github.com/wasp-lang/wasp)

## [](#2-where-do-we-check-permissions-in-a-web-app-frontend-vs-backend-vs-database)2. Where do we check permissions in a web app: frontend vs backend vs database

We explained a bunch of terms, let's see now how access permission checks are actually done in practice!

In a typical web app, you will have a frontend, backend (server), and database.

The frontend will be issuing commands to the server, which then executes operations and possibly modifies the database (on their behalf). Since **users don’t have direct access to the database**, and since the **frontend is inherently not secure**, that leaves the **server as the central place where all the crucial access control needs to happen**.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--nJj0OpmU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5eevhxzig3kwgr8t5hsf.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--nJj0OpmU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5eevhxzig3kwgr8t5hsf.png)

### [](#frontend-browser)Frontend (browser)

By frontend we mean web client -> code (e.g. JavaScript) that executes in the browser.

The frontend is here to help users issue commands towards the server via which users can access and/or modify the resources of our web app (which are most often stored in the database).

Since users can manipulate the frontend code as they wish, we can't really do any permissions checks in the frontend code, we can't trust it!

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--E31F1qGM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eomcc7mmh9h9w6ccp9zk.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--E31F1qGM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eomcc7mmh9h9w6ccp9zk.png)

Any permission checks we do on the frontend, we will need to repeat on the server in any case.  
  
If that is so, should we at all check permissions on the frontend, and what is the purpose of that?  
  
**The main reason for doing any permissions checks on the frontend is ergonomics/user experience** -> by having UI focus only on resources they can change, we make it easier for users to understand what they can do in our web app and make sure they don't waste time on trying to describe complex operations that server will then not be able to execute.

So, for example, our frontend code can hide/omit certain fields in the UI form if the user shouldn't be able to access them, it can prevent opening certain pages, or hide/omit certain buttons if they trigger operations that the user is not allowed to perform.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--g-g4LVX5--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5d1231jozj8xk7dpjn8z.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--g-g4LVX5--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5d1231jozj8xk7dpjn8z.png)

**Takeaway: Permission checks on frontend are not there for security, but only for ergonomics / improving user experience.**

### [](#backend-server)Backend (server)

The server is **a crucial place to implement access control**. It exposes an API that the frontend (browser) and/or other services consume. While doing that, they authenticate with the server, so that server knows who they are, and then they ask (i.e. via REST API or GraphQL API) the server to execute certain operations (i.e. creating, updating, or fetching something). It is the server’s job to figure out if they are allowed (authorized) to perform those operations (on specified resources / with provided arguments) and to reject them if they are not.

At its core, permissions checks on the server are here to **check for each API endpoint** if the caller is allowed to execute it. Often they are executed at the very start of the API endpoint logic, but often they are also intertwined with the rest of the endpoint handler logic.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--cPXd0_5Z--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ivjh3yn8zj9ceg59wvaq.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--cPXd0_5Z--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ivjh3yn8zj9ceg59wvaq.png)

Besides defining checks at API/operation level, they are also often defined at the **data/model level**. This means that they are tied to specific data models (normally from the database), as part of data access logic (ORM), and are defining who can access specific field(s), or even the whole data model.

Example of attaching permission checks to the data model directly in the GraphQL schema ([from this blog post](https://www.prisma.io/blog/graphql-directive-permissions-authorization-made-easy-54c076b5368e)):

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--_MoIwnBo--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/swgvs0y2cs183drgk4zr.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--_MoIwnBo--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/swgvs0y2cs183drgk4zr.png)

For a more sophisticated RBAC approach, with an additional layer of indirection (permissions), read on.

### [](#database)Database

Usually, users don’t have direct access to the database at all, instead, they affect it via the server. **In such a case, there is no need to do specific database access control** besides normal constraints that you will have in your DB to ensure data model integrity, like uniqueness, validations, and similar. That said, in some situations, you might want to do it, but we will not get into that in this article.

## [](#3-common-approaches-rbac-abac-)3. Common approaches (RBAC, ABAC, …)

The most common approaches to access control are **RBAC** (Role-Based Access Control) and **ABAC** (Attribute-Based Access Control), with RBAC having the strong lead (but ABAC is picking up).

Although less popular, we will also shortly mention ReBAC as an “in-between” option.

### [](#rbac-rolebased-access-control)RBAC - Role-based access control

Roles rule :D! In [RBAC](https://en.wikipedia.org/wiki/Role-based_access_control), roles are the central concept. Some example roles might be `admin`, `guest`, `writer`, `moderator`, …. When determining if a certain user has access, **we check their roles and determine their access rights based on it**. For example, `admin` can delete other users, articles, and projects, but `guest` can’t modify any resources, only read articles.

Pro advice (thanks Karan!): While we could be checking the user’s roles directly in the permission checks, it is even better (and recommended by OWASP) to add a layer of indirection → permissions. **So roles are attached to users, permissions are attached to roles, and permission checks check permissions** (who would expect that :)!?).

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--pogPaFlC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/avvdiy6t9d2bvmbi82xn.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--pogPaFlC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/avvdiy6t9d2bvmbi82xn.png)

For example, a user might have role `admin`, and role `admin` has permissions `updateArticle` and `deleteArticle` attached to it. Then, when determining if a user can delete the article, we first fetch his role, then we fetch the permissions attached to that role, and finally check if `deleteArticle` is present among those → if so, they can continue with the deletion!

This way, if we decide a certain role should have more or fewer permissions, we just add or remove the permission in question to the role, and that is it! We don’t have to go through every permission check and update its logic (which we would have to do if we were checking directly against roles).

**RBAC is popular because it is relatively simple and it reflects the basic business domain pretty well** - often we are thinking in the terms of roles in the real world, so it is easy to grasp and understand. There are plenty of solutions and frameworks out there that implement RBAC.

While a good match for many common use cases, there is a drawback to RBAC - when access control becomes complex (which usually happens as the web app evolves and grows big), RBAC sometimes fails in offering needed granularity in an elegant way, resulting in unwieldy and overly-complex access control logic.

### [](#abac-attributebased-access-control)ABAC - Attribute-based access control

In [ABAC](https://en.wikipedia.org/wiki/Attribute-based_access_control), key idea is that you define **a bunch of access control rules** where each rule takes different “attributes” as input. When you need to check if a user is authorized to do something, you run the rules and **if all the rules pass, it is a go**, but if a single rule fails, it is a no go.

Rule attributes can be anything, but usually, they fall into 4 categories:

1. **Subject**: information about a user (i.e. user’s id or name)
2. **Action**: operation they want to perform (i.e. reading an Article)
3. **Object**: resources they want to operate on (i.e. an Article),
4. **Environment/context:** i.e. current time of the day or number of previous requests that the user did in the last hour.

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--yNY_XoMf--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kqw7br6sa7j1cwar07x6.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--yNY_XoMf--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kqw7br6sa7j1cwar07x6.png)

Let’s observe the example from before where we wanted to know if user is allowed to delete an article.

In ABAC, we could define an action “deleteArticle”, and then define a rule that takes user(subject), action, object, and additional context. That rule would check if action is “deleteArticle” → if so, it would evaluate if user is allowed to delete the article specified as an object, by checking some properties of user, maybe even role, or by checking if user is owner of that article.

Then, when user actually issues a command to delete an article, we would ask our access control system to run it against all the rules it has, while giving it the (user, “deleteArticle”, article, context) tuple → most of the rules would say all is ok since they are not concerned with “deleteArticle” action, but the ones that are (like the one we defined above) must all pass in order to actually allow the access.

**ABAC is very flexible and general as an approach**, and you could easily implement RBAC (and many other approaches) in ABAC (by checking the user’s role as one of the attributes) → therefore it is more general/expressive than RBAC.

However, ABAC is more complex to implement, and it is also more expensive performance-wise, due to needing to check multiple rules each time that access control check is being performed.

### [](#rebac-relationshipbased-access-control)ReBAC - Relationship-based access control

Roles (RBAC) can be lacking when you need to grant access based on relationship-related questions like “is this user owner of this article” or “does this user belong to this workspace”.

While ABAC can easily handle this, you could also consider it a bit too powerful if all you need to describe are relationships → and this is where ReBAC comes in.

While there are different ways one could go about implementing ReBAC, the simplest one is to build on top of RBAC by introducing a concept of “relationship” rules to your access control logic and then checking those alongside the roles. So RBAC with a dash of ABAC (focused on relationships).

## [](#4-owasp-recommendations)4. OWASP recommendations

When looking online for “official”/standardized recommendations on how to do access control in web apps, you will most likely find resources produced by OWASP.

Definition of OWASP: The Open Web Application Security Project® (OWASP) is a nonprofit foundation that works to improve the security of software.

I found that they have quite a few resources on how to do access control in web apps, the most interesting being the following:

- [OWasp presentation about how to do ACL in Web App](https://owasp.org/www-pdf-archive/ASDC12-Access_Control_Designs_and_Pitfalls.pdf).
- [OWasp cheat sheet on how to do ACL in Web App.](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Authorization_Cheat_Sheet.md)

From their materials I extracted a couple of main points that made the most sense to me:

- **Centralize the access control logic so it is easy to review.**
- **Deny access by default.**
- **Prefer ABAC over RBAC.**

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--N-gznaUa--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/taabe0y7y9umc4t9ooh3.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--N-gznaUa--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/taabe0y7y9umc4t9ooh3.png)

## [](#5-implementing-access-control-in-practice)5. Implementing access control in practice

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--7Vge-T3w--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7v3fsdwmhilos95odkd0.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--7Vge-T3w--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7v3fsdwmhilos95odkd0.png)

Here’s a Reddit [poll I did on r/webdev](https://www.reddit.com/r/webdev/comments/vhaglx/what_do_you_use_for_access_control_permission/).

An interesting finding is that even though the sample is pretty small, it is clear that devs prefer RBAC over OWASP-recommended ABAC.

I believe this is due to 2 main reasons: RBAC is simpler + there are more libraries/frameworks out there supporting RBAC than ABAC (again, due to it being simpler).

It does seem that ABAC is picking up recently though, so it would be interesting to repeat this poll in the future and see what changes.

### [](#organic-development)Organic development

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--wvy3PoEe--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/69khfedn70ocdaxk6tcg.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--wvy3PoEe--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/69khfedn70ocdaxk6tcg.png)

Often, we add permission checks to our web app one by one, as needed. For example, if we are using NodeJS with ExpressJS for our server and writing middleware that handles HTTP API requests, we will add a bit of logic into that middleware that does some checks to ensure a user can actually perform that action. Or maybe we will embed “checks” into our database queries so that we query only what the user is allowed to access. Often a combination.

What can be dangerous with such an organic approach is the complexity that arises as the codebase grows - if we don’t put enough effort into centralizing and structuring our access control logic, it can become very hard to reason about it and to do consistent updates to it, leading to mistakes and vulnerabilities.

Imagine having to modify the web app so that user can now only read their own articles and articles of their friends, while before they were allowed to read any article. If there is only one place where we can make this update, we will have a nice time, but if there are a bunch of places and we need to hunt those down first and then make sure they are all updated in the same way, we are in for a lot of trouble and lot of space to make mistakes.

### [](#using-an-existing-solution)Using an existing solution

Instead of figuring out on our own how to structure the access control code, often it is a better choice to use an existing access control solution! Besides not having to figure and implement everything on your own, another big advantage is that these solutions are battle-tested, which is very important for the code dealing with the security of your web app.

We can roughly divide these solutions into frameworks and (external) providers, where frameworks are embedded into your web app and shipped together with it, while providers are externally hosted and usually paid services.

A couple of popular solutions:

1. [https://casbin.org/](https://casbin.org/) (multiple approaches, multiple languages, provider)
    - Open source authZ library that has support for many access control models (ACL, RBAC, ABAC, …) and many languages (Go, Java, Node.js, JS, Rust, …). While somewhat complex, it is also powerful and flexible. They also have their Casdoor platform, which is authN and authZ provider.
2. [https://casl.js.org/v5/en/](https://casl.js.org/v5/en/) (ABAC, Javascript)
    - Open source JS/TS library for ABAC. CASL gives you a nice way to define the ABAC rules in your web / NodeJS code, and then also check them and call them. It has a bunch of integrations with popular solutions like React, Angular, Prisma, Mongoose, … .
3. [https://github.com/CanCanCommunity/cancancan](https://github.com/CanCanCommunity/cancancan) (Ruby on Rails ABAC)
    - Same like casl.js, but for Ruby on Rails! Casl.js was actually inspired and modeled by cancancan.
4. [https://github.com/varvet/pundit](https://github.com/varvet/pundit)
    - Popular open-source Ruby library focused around the notion of policies, giving you the freedom to implement your own approach based on that.
5. [https://spring.io/projects/spring-security](https://spring.io/projects/spring-security)
    - Open source authN and authZ framework for Spring (Java).
6. [https://github.com/dfunckt/django-rules](https://github.com/dfunckt/django-rules) a. A generic, approachable open source framework for building rule-based systems in Django (Python).
7. [Auth0](https://auth0.com/) (provider)
    - Auth0 has been around for some time and is probably the most popular authN provider out there. While authN is their main offering (they give you SDKs for authentication + they store user profiles and let you manage them through their SaaS), they also allow you to define authZ to some degree, via RBAC and policies.
8. [https://www.osohq.com/](https://www.osohq.com/) (provider, DSL)
    - OSO is an authZ provider, unique in a way that they have a specialized language for authorization (DSL, called Polar) in which you define your authorization rules. They come with support for common approaches (e.g. RBAC, ABAC, ReBAC) but also support custom ones. Then, you can use their open source library embedded in your application, or use their managed cloud offering.
9. [https://warrant.dev/](https://warrant.dev/) (Provider)
    - Relatively new authZ provider, they have a dashboard where you can manage your rules in a central location and then use them from multiple languages via their SDKs, even on the client to perform UI checks. Rules can also be managed programmatically via SDK.
10. [https://authzed.com/](https://authzed.com/) (Provider)
    - AuthZed brings a specialized SpiceDB permissions database which they use as a centralized place for storing and managing rules. Then, you can use their SDKs to query, store, and validate application permissions.
11. [https://clerk.com/](https://clerk.com/) (Provider)
    - Clerk is a user management solution that gives you pre-built React/JS components, along with an API and SDK for a number of sign-in options. It also has a strong focus on up-to-date security best-practices.

## [](#summary-tldr)Summary (TLDR)

- **Authentication** (authN) answers “who are they”, **authorization** (authZ) answers “are they allowed to”, while **access control** is the overarching term for the whole process of performing authN and authZ.
- Doing access control on the frontend is just for show (for improving UX) and you can’t rely on it. **Any and all real access control needs to be done on the server** (possibly a bit in the db, but normally not needed).
- While it is ok to start with a simple access control approach at the beginning, you should be ready to switch to a more advanced approach once the complexity grows. The most popular approaches for doing access control are **RBAC** (role-based) and **ABAC** (attribute-based). RBAC is easier to get going with, but ABAC is more powerful.
- You should make sure your access control has **as little duplication as possible and is centralized**, in order to reduce the chance of introducing bugs.
- It is usually smart to **use existing solutions**, like access control frameworks or external providers.

## [](#access-control-in-wasp)Access control in Wasp

In [Wasp](https://wasp-lang.dev) we allow you to "roll-your-own" auth in just a few lines of code. Which means the code is yours and you don't rely on expensive third-party providers.

We don’t yet have special support for access control, but we will be adding it soon!

In the meantime, if you liked this article and want to show your support, you can [give us a star on GitHub!](https://www.github.com/wasp-lang/wasp)

[![https://res.cloudinary.com/practicaldev/image/fetch/s--OCpry2p9--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bky8z46ii7ayejprrqw3.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--tnDxibZC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://res.cloudinary.com/practicaldev/image/fetch/s--OCpry2p9--/c_limit%252Cf_auto%252Cfl_progressive%252Cq_66%252Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bky8z46ii7ayejprrqw3.gif)](https://www.github.com/wasp-lang/wasp)

[⭐️ Star Wasp on GitHub 🙏](https://www.github.com/wasp-lang/wasp)

In the near future, we will probably go for ABAC for Wasp, and we would love to provide a way to define access rules both at the Operations level and at Entity (data model) level. Due to Wasp’s mission to provide a highly integrated full-stack experience, we are excited about the possibilities this offers to provide an access control solution that is integrated tightly with the whole web app, through the whole stack!

You can check out our discussion about this in our [“Support for Permissions” RFC](https://github.com/wasp-lang/wasp/issues/584).

## [](#thanks-to-the-reviewers)Thanks to the reviewers

[Karan Kajla](https://twitter.com/karankajla) (pro advice on RBAC!), [Graham Neray](https://twitter.com/grahamneray) (great general advice + pointed out ReBAC), [Dennis Walsh](https://twitter.com/lawjolla) (awesome suggestions how to have article read better), [Shayne Czyzewski](https://github.com/shayneczyzewski), [Matija Sosic](https://twitter.com/matijasosic), thank you for taking the time to review this article and make it better! Your suggestions, corrections, and ideas were invaluable.

## Top comments (7)

### Sort discussion:

- [
    
     Top
    
    Most upvoted and relevant comments will be first
    
    ](/wasp/a-guide-to-auth-access-control-in-web-apps-2410?comments_sort=top#toggle-comments-sort-dropdown)
- [
    
    Latest
    
    Most recent comments will be first
    
    ](/wasp/a-guide-to-auth-access-control-in-web-apps-2410?comments_sort=latest#toggle-comments-sort-dropdown)
- [
    
    Oldest
    
    The oldest comments will be first
    
    ](/wasp/a-guide-to-auth-access-control-in-web-apps-2410?comments_sort=oldest#toggle-comments-sort-dropdown)

Subscribe

    ![pic](https://res.cloudinary.com/practicaldev/image/fetch/s--V3djhsWJ--/c_limit,f_auto,fl_progressive,q_auto,w_256/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8j7kvp660rqzt99zui8e.png)

Personal Trusted User

[Create template](/settings/response-templates)

Templates let you quickly answer FAQs or store snippets for re-use.

Submit Preview [Dismiss](/404.html)

 

 

[![shayneski profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--rbyiu449--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1131532/6d3fe3e4-ec13-4a96-a85b-93afcfd9e766.jpeg)](https://dev.to/shayneski)

[Shayne Czyzewski](https://dev.to/shayneski)

Shayne Czyzewski

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--762azyYr--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1131532/6d3fe3e4-ec13-4a96-a85b-93afcfd9e766.jpeg)Shayne Czyzewski](/shayneski)

Follow

- Joined
    
    Aug 2, 2023
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahp8)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahp8)

- Hide

Awesome explanations, as usual! Nicely done

4 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ahp8)

 

 

[![nevodavid profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--eIJW5yjJ--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/820341/5d291561-0d60-40cf-a9d3-959dab08f1ac.png)](https://dev.to/nevodavid)

[Nevo David](https://dev.to/nevodavid)

Nevo David

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--CTb6k9_U--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/820341/5d291561-0d60-40cf-a9d3-959dab08f1ac.png)Nevo David](/nevodavid)

Follow

I love Novu 🚀

- Work
    
    Head of Growth @ Novu
    
- Joined
    
    Feb 23, 2022
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahod)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahod)

- Hide

Great article about ACL!  
Thank you!

4 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ahod)

 

 

[![emmanuelthecoder profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--yM2nhChk--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/536973/42b9d0f3-7e6a-4b08-9e3a-5a372fa66854.jpg)](https://dev.to/emmanuelthecoder)

[Emmanuel Aiyenigba](https://dev.to/emmanuelthecoder)

Emmanuel Aiyenigba

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--C6N0pqq5--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/536973/42b9d0f3-7e6a-4b08-9e3a-5a372fa66854.jpg)Emmanuel Aiyenigba](/emmanuelthecoder)

Follow

A meticulous software developer, technical writer, team player and deep creative thinker.

- Email
    
    [loyaltysamuel001@gmail.com](mailto:loyaltysamuel001@gmail.com)
    
- Location
    
    Ilorin, Nigeria
    
- Work
    
    Software Engineer
    
- Joined
    
    Dec 9, 2020
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahog)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahog)

- Hide

Great article. Thanks for sharing.

4 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ahog)

 

 

[![martinovicdev profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--OAuVgLRV--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1126557/e7f6249c-4383-4957-80b5-13f8a4eba9d8.jpeg)](https://dev.to/martinovicdev)

[Boris Martinovic](https://dev.to/martinovicdev)

Boris Martinovic

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--74bZVEFG--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1126557/e7f6249c-4383-4957-80b5-13f8a4eba9d8.jpeg)Boris Martinovic](/martinovicdev)

Follow

- Joined
    
    Jul 25, 2023
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ai2o)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ai2o)

- Hide

Great article, one of my favourite reads on this topic!

2 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ai2o)

 

 

[![matijasos profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--sBDXz3yP--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/331796/5d3fd56d-440c-437c-bcda-152c482774b9.jpeg)](https://dev.to/matijasos)

[Matija Sosic](https://dev.to/matijasos)

Matija Sosic

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--4Gmo1ac8--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/331796/5d3fd56d-440c-437c-bcda-152c482774b9.jpeg)Matija Sosic](/matijasos)

Follow

- Joined
    
    Feb 7, 2020
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahoh)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahoh)

- Hide

Amazing work Martin, this is one of the best overviews I read on the topic!

4 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ahoh)

 

 

[![infomiho profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--LZtwVW-o--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/32926/49786321-b17d-4b26-9c21-ba64c896224b.jpeg)](https://dev.to/infomiho)

[Mihovil Ilakovac](https://dev.to/infomiho)

Mihovil Ilakovac

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--CpLFnAOi--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/32926/49786321-b17d-4b26-9c21-ba64c896224b.jpeg)Mihovil Ilakovac](/infomiho)

Follow

Full-stack developer curious about the world, currently building a new full-stack framework

- Location
    
    Zagreb, Croatia
    
- Joined
    
    Sep 11, 2017
    

• [Nov 7](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahof)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ahof)

- Hide

Are there any 3rd party tools for this you would recommend? If I'm lazy 😬

2 likes Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ahof)

 

 

[![clabnet profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--cUtLPru3--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/191444/f78718ad-8249-4c83-be2e-94b47d4a1eb7.jpeg)](https://dev.to/clabnet)

[Claudio Barca](https://dev.to/clabnet)

Claudio Barca

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--0T2H4Vs9--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/191444/f78718ad-8249-4c83-be2e-94b47d4a1eb7.jpeg)Claudio Barca](/clabnet)

Follow

- Joined
    
    Jul 7, 2019
    

• [Nov 9 • Edited on Nov 9 • Edited](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ain9)

- [Copy link](https://dev.to/wasp/a-guide-to-auth-access-control-in-web-apps-2410#comment-2ain9)

- Hide

Can you add also Keycloak as authZ & authN open source.

1 like Like [ Reply](#/wasp/a-guide-to-auth-access-control-in-web-apps-2410/comments/new/2ain9)

[Code of Conduct](/code-of-conduct) • [Report abuse](/report-abuse)

Are you sure you want to hide this comment? It will become hidden in your post, but will still be visible via the comment's [permalink](#).

Hide child comments as well

Confirm

For further actions, you may consider blocking this person and/or [reporting abuse](/report-abuse)