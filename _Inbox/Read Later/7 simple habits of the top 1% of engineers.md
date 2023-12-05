[[ReadItLater]] [[Article]]

# [7 simple habits of the top 1% of engineers](https://engineercodex.substack.com/p/7-simple-habits-of-the-top-1-of-engineers)

I’ve worked with phenomenal engineers, both at large companies, like FAANG, and smaller companies, like startups.

Some of these engineers have went on to start their own companies, lead developments that change the web as we know it (like Vercel!), or have grown to lead billion-dollar initiatives at big tech companies today.

Throughout my time working with them, I noticed that all of them had some overlapping habits in the code they produced.

> “Any fool can write code that a computer can understand. Good programmers write code that humans can understand.” – Martin Fowler.

Code is for humans, not just for computers.

**Code is for the engineers on your team**, who read, maintain, and build on top of your code.

**Code is for the users**, whether it’s a kid on their phone, a developer calling your API, or yourself.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F64e58201-aee1-43cf-bf38-44ecd98dbe5f_1003x850.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F64e58201-aee1-43cf-bf38-44ecd98dbe5f_1003x850.png)

Code has three audiences: human readers, machine readers, and users.

The best engineers I know are product-minded: thinking about solving a problem for *humans* first.

**The best engineers I knew always evaluated the value of their code, for all audiences.**

If they missed the mark on one of the audiences, that code did not make it into production.

Amazing engineers stay unattached to the code itself.

They were unafraid to delete and start over on code, even if they were 90% of the way in, if it meant that the end result would be better overall.

Code isn’t personal, so feedback was taken with stride.

Code isn’t perfect. Nobody cares about perfect code. They care about code that delivers change.

**The best way to teach yourself to be unattached from your code is to realize that in 20 years, there’s a high chance that [much of your code will either be technical debt, deprecated, or rewritten.](https://blog.visionarycto.com/p/my-20-year-career-is-technical-debt)**

When writing code, stick to a consistent standard and style of coding. Consistency makes code easier to read and understand by both future you and your teammates.

A consistent style guide allows both a team and a codebase to scale easier. This is how companies like Meta and Google ship so much code quickly without the codebase becoming unreadable and unmaintainable over time.

**Every outperformer I knew had the team’s code standards internalized and followed it as closely as possible, knowing its benefits.**

-   [Google has a readability process to maintain clean code.](https://engineercodex.substack.com/p/how-google-writes-clean-maintainable)
    
-   [Google has open sourced some of their style guides. (Link)](https://google.github.io/styleguide/)
    
-   [Meta has a C++ style guide for some of their open source code. (Link)](https://github.com/facebook/hhvm/blob/master/hphp/doc/coding-conventions.md)
    
-   *Tip*: Formatting a linter for your team is definitely worth the time to set up, if there isn’t one already.
    

[

![Inconsistent versus consistent code, visualized.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff349b4c5-9cf5-47cb-b965-9957f17a71e1_4867x999.png "Inconsistent versus consistent code, visualized.")

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff349b4c5-9cf5-47cb-b965-9957f17a71e1_4867x999.png)

Every elite engineer I knew produced code that may have been complex to produce, but was [simple to both read and understand at the end](https://engineercodex.substack.com/p/how-instagram-scaled-to-14-million). The best word I had for this was that their code was *aesthetically pleasing**.***

Their code was **clean, organized, and logical**. Each decision made in their code made sense, and when something didn’t, it was documented well within the code.

A good way to write clean code is to follow principles, like the SOLID principles. Though they were initially designed with OOP (object-oriented programming) in mind, they are extensible to general programming:

-   *Single Responsibility*: A class should only have one responsibility.
    
-   *Open-Closed*: Software objects (classes, modules, etc.) should be open for extension but closed for modification, allowing predictable, maintainable code.
    
-   *Liskov Substitution*: Subtypes must be substitutable for their base types without affecting the correctness of the program.
    
-   *Interface Segregation*: Code shouldn’t be dependent on giant interfaces in which they don’t use all of it. Instead, packages should both contain and allow smaller, specific interfaces to be importable.
    
-   *Dependency Inversion*: High-level modules should not depend on low-level modules; both should depend on abstractions, fostering a more flexible and decoupled system design.
    

An example of this is **naming**. Good naming has no magic values, clear distinctions, descriptive function names, and understandable variables.

Code shouldn’t produce surprises. This is done by following code principles and writing proper tests.

**Good code is predictable**.

Tests force code clarity and predictability. They provide confidence. Good automated testing allows teams to make changes to code without worrying about breaking something unseen.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcc326faa-fe17-46b3-9a02-a8b36ebf31ff_1150x750.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fcc326faa-fe17-46b3-9a02-a8b36ebf31ff_1150x750.png)

Good code is predictable.

Some types of tests include:

-   *Unit tests* for individual components and isolated functions.
    
-   *Integration tests* for interactions between multiple components.
    
-   *End-to-end* tests that assess the entire system’s functionality from a user’s perspective
    

**Tests should be simple. It should be easy to identify what went wrong when reading a failing test.**

**It’s also important to know what not to test.**

For example, if the effort of an end-to-end test outweighs the actual benefit of the program, then the test is replaced by thoughtful documentation, monitoring, and alerting to the right people (such as the code owner).

Tests should also not test implementation details within the code, such as testing for certain CSS selectors in frontend code versus using data-attributes or just screenshot tests.

No great systems were built alone. Great engineers went through design reviews, solicited feedback, and continued iterating on their initial designs for their code.

Everyone has gaps in their knowledge that can be filled in by other people. Fresh perspectives can often help code become clearer or provide a new approach that may not have been thought of previously.

The best engineers were **both communicative and collaborative - not afraid to take the time to work together for the chance at a better end result.**

This can be as simple as pinging a teammate for a quick review over a document or adding extra code reviewers to an important pull request.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe9afa94c-7524-417f-9e7d-e746c606bdc3_1142x476.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe9afa94c-7524-417f-9e7d-e746c606bdc3_1142x476.png)

**The best engineers I know complete projects fast… by coding slow.**

Sounds weird, right?

All these principles and habits above add more time to the overall *first pass* of coding. But they allow engineers to take a project’s progress forward, step by step.

**By taking the time to use standards, test properly, use principles, and communicate often, they save themselves more time in the long run.**

The alternative as I personally have experienced myself when I was an intern and junior engineer, as I’m sure many others have, is rushing 3 steps forward, hitting a blocker, then having to retreat 5 steps back.

[

![Go fast to go slow. Go slow to go fast.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb8497dc0-e5fc-4a8b-8938-7b0c4bcf4f5d_1004x351.png "Go fast to go slow. Go slow to go fast.")

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb8497dc0-e5fc-4a8b-8938-7b0c4bcf4f5d_1004x351.png)

**The above “rules” and “principles” are simply guidelines.** 

Not everything can fit neatly and nicely into guidelines.

Sometimes, the code you’re writing is a square that just can’t fit into that circle. That’s okay.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdb830d9c-0072-45e2-a0db-356bfefd4cba_1850x650.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdb830d9c-0072-45e2-a0db-356bfefd4cba_1850x650.png)

Sometimes, boundaries need to be stretched.

In that case, make sure to document why your code is written in a certain way.

If you don’t, then someone, like future you, might come look at the code in the future and think “wow, I was dumb back then. Why isn’t this following our standards?”.

They then will spend 20 hours re-coding it to fit the standards just to come to the same conclusion as before. Sound familiar?

**The reality of software development is that not all code can be clean or follow the rules perfectly.**

**What it can be, though, is consistent, clean, understandable, testable, and valuable.**

Other patterns I noticed about these engineers, that I will write about in the future:

-   **Deep domain knowledge in at least one field.** Every single engineer that I took notes on is at the top of *their field* today because they focused and became experts at a certain field, whether it be frontend infrastructure, distributed systems, or clean UIs.
    
-   **Marketed themselves often and appropriately.** These engineers were not hiding in plain sight at all. Everyone on their team and everyone that worked with them knew their value and expertise. This came through a combination of marketing themselves appropriately and working on high-impact projects.