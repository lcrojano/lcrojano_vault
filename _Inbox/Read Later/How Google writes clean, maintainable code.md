In my article about [the simple habits of great engineers](https://engineercodex.substack.com/p/7-simple-habits-of-the-top-1-of-engineers), I mentioned that great engineers use consistent standards.

With billions of lines of code in its codebase, Google follows a process called **Readability, which they describe as the “Google-wide mentorship process for disseminating programming language best practices.”**[1](https://engineercodex.substack.com/p/how-google-writes-clean-maintainable#footnote-1-137714206)

Each pull request is reviewed for proper code style and best practices by a code readability approver. (Note: Google actually calls pull requests [changelists](https://abseil.io/resources/swe-book/html/ch03.html#ch01fn46))

> Readability is described in [Software Engineering at Google](https://abseil.io/resources/swe-book/html/toc.html), along with various essays and comments online. All sources are linked throughout the article.

In this article, I’ll go through: 

- **Pros and cons of Google’s readability process**
    
- **Opinions from experienced users of Google’s readability process**
    
- **Is readability necessary?**
    
- **Why code quality doesn’t equal better business outcomes**
    

Pledge your support

## **What is “readability” exactly?**

Readable code is defined as code that follows a language’s best practices and style guide. [Google has generously published their style guides publicly for many languages, such as C++, TypeScript, Java, and Python.](https://google.github.io/styleguide/)

**To submit code into Google’s codebase, you need to get at least one review and approval from someone who:**

- **Owns the code**
    
- **Has “readability” of the languages used in the changelist**
    
- **Is not you**
    

Engineers who have “readability” in a certain language can sign off on changelists that contain code in that language.

A Hacker News commenter described an example:

> For example, if you are an owner and have readability, you just need someone who isn't you to sign off on it.
> 
> If you don't have ownership or readability you need to get someone who has those things to sign off.
> 
> If you can find someone who has both, great. Otherwise, you'll need two people. ([Source](https://news.ycombinator.com/item?id=22620678))

To earn readability, engineers must send in changelists of a language to “readability reviewers” of that language until those reviewers feel that you have adequate knowledge of “readability.” ([Source](https://news.ycombinator.com/item?id=22620455))

**Usually, readability reviewers are experts in a language, knowing the ins and outs of it deeply.**

Google says that about 20% of their engineers are participating in the readability process and only about 1-2% of their engineers are readability reviewers.

**It’s considered a benefit to have readability in your primary team’s language.** It means you can approve your team’s code from an actual implementation perspective, ownership perspective, and readability perspective all at once.

### Example: Basic [TypeScript style guide](https://google.github.io/styleguide/tsguide.html) rules

- `UpperCamelCase` for classes, interfaces, types, enums, and decorators
    
- `lowerCamelCase` for variables, parameters, functions, methods, properties
    
- `CONSTANT_CASE` for global constant values
    
- `descriptiveNames`, not just `x = 10`
    

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F35b3efcf-3324-4747-bd53-5eda8bdae9c6_617x159.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F35b3efcf-3324-4747-bd53-5eda8bdae9c6_617x159.png)

[Source](https://google.github.io/styleguide/tsguide.html#control-flow-statements-blocks)

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe7f90796-354f-4c38-8c55-707db7e4a8c1_838x251.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe7f90796-354f-4c38-8c55-707db7e4a8c1_838x251.png)

[Source](http://source/)

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F28c66821-1de0-4230-8240-5b972da421a8_753x270.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F28c66821-1de0-4230-8240-5b972da421a8_753x270.png)

[Source](https://google.github.io/styleguide/tsguide.html#arrayt-type)

## **Benefits of Google’s readability process**

- **Keeps the codebase readable, searchable, and predictable.**
    
    - You can search for a certain code snippet to see how its used by other teams, in case you need an example to work off of.
        
    - Large scale changes across the entire codebase can be made more confidently.
        
    - Engineers can change teams without worrying about adhering to a different coding style.
        
- **Increases knowledge sharing.** 
    
    - It’s really hard to learn just through reading. Application trumps all when it comes to learning.
        
    - Various language features that may not be known to the writer of the code are often taught in the comments section of a pull request. Then, you never forget that feature or lesson again, because there is a very clear example in your head that has ingrained it in your head.
        
    - This also enforces proper code sharing. If a certain function is already available in a shared package, then that should be used instead of a custom one being written. In codebases of Google’s size, those “certain functions” may not be known of by everyone.
        
- **Enforces best practices**.
    
    - This increases codebase scalability and develops better engineers
        
    - **For engineers, this forcing function makes best practices and style while coding [a habit.](https://engineercodex.substack.com/p/7-simple-habits-of-the-top-1-of-engineers)**
        
- **Gets engineers used to reading code.**
    
    - Reading code is harder than writing it!
        

- **Teaches you the ins and outs of a language**.
    
    - Readability is a forcing mechanism for really getting to know a language deeply and how it works.
        
        - For example, if you haven’t written C++ in a while, it can be easy to get something like memory management wrong. You can expect with 100% certainty your code reviewer will teach you if you don’t teach yourself.
            
- **Sustains a culture of mentorship.**
    

Pledge your support

## Drawbacks of Google’s readability process

#### **Slows down velocity**

**This is seemingly the most common complaint of the readability process.** 

If your team happens to write C++ but nobody on the team has C++ readability, then the team constantly has to find C++ readability approvers from outside the team. This can slow down teams considerably, though it seems like this doesn’t usually happen.

Some teams associated with [Google don’t follow such the readability process, such as Chrome, ChromeOS, and Android.](https://news.ycombinator.com/item?id=22612812)

In 2020, an ex-Googler noted that the Readability process seems to apply best to web services within Google:

> During my time there, the Android team was recruiting internally, advertising "come work on Android, we don't require Readability." It was seen as an internal competitive advantage to reject these processes!
> 
> I speculate that Android and Chrome and others have distinct processes for a good reason, and that the book is unknowingly slanted towards web-service style engineering. ([Source](https://news.ycombinator.com/item?id=22612812))

#### Subject to human bias.

[An ex-Googler who wrote about Readability mentioned a setback he had while in the process of getting readability.](https://www.moderndescartes.com/essays/readability/#:~:text=a%20similar%20size.-,Readability%20and%20Me,-My%20own%20readability)

He submitted a small change for readability review and the reviewer forced him to change the entire file, which was not written by him. This slowed down his readability progress and velocity.

#### Hard to scale since its completely human based.

Funnily enough, this is one of the processes Google does that is _not_ built in a scalable way.

_If you’re enjoying this breakdown, subscribe to Engineer’s Codex. It’s free!_

Pledge your support

## **What do (ex-)Googlers think about readability?**

#### Positive Feedback

Many ex-Googlers and current Googlers enjoy the readability process. The benefits outweigh the extra time cost, as it makes code easier to understand and maintain.

An interesting point I heard was that **readability standards and the style guide make it easy to do code review without sounding hostile.** Pointing out small nitpicks while referring to readability allows reviewers to enforce coding practices in a non-personal way.

#### Negative Feedback

Other ex-Googlers believe the readability process is too heavyweight and a hindrance.

[Ex-Googler Brian Kihoon Lee doesn’t recommend readability process anywhere else.](https://www.moderndescartes.com/essays/readability/)

Instead, he recommends a “readability lite” and prefers the style of teams at Amazon and Apple, where each team has different processes and styles. This allows them to move faster as a team.

## **Is the process necessary?**

Google themselves acknowledge the [“nontrivial costs of readability.”](https://abseil.io/resources/swe-book/html/ch03.html#ch01fn46:~:text=Increased%20friction%20for,specialized%20code%20reviews.)

However, Google has a strong engineering-led culture and they find the long-term benefits outweigh any short-term velocity gains.

As all software engineering goes, **Google is making a tradeoff here between velocity and code quality.**

### Code quality != business outcomes

Code quality doesn’t seem to affect business outcomes all that much.

**Facebook (now Meta)** has had [“code quality problems” for almost a decade now](https://news.ycombinator.com/item?id=13856443), and it hasn’t really affected them all that much. Any pitfalls they’ve run into have been more of a result of business competition or decisions made by leadership.

**[Oracle’s](https://news.ycombinator.com/item?id=18442941)** [database has a horrendous 25 million lines of nasty code that is a headache to deal with.](https://news.ycombinator.com/item?id=18442941)

**[ASML](https://news.ycombinator.com/item?id=18463181)** [seems even worse.](https://news.ycombinator.com/item?id=18463181)

**Amazon, Apple, and most tech companies have differing code quality across teams.**

All these companies have tooling, style guides, mentorship, and other practices that help them maintain a standard of code quality, allowing them to move fast without delving into “terrible code” territory. 

They also have systems in place to keep their services from melting down, in which reliability excellence can negate poorer code quality in some places.

### Code quality is subjective

The need for code quality depends on the individual and the team.

There are anecdotes from all sides of people liking or disliking various processes.

People have loved Google’s readability process, while others hated how slow it made everything. 

Engineers who left Facebook complained about the shoddy code quality and lack of automated testing, while others loved how fast they could commit code.

Some people and teams are fine with giving up code quality for higher velocity. 

There’s a balance to be found and **it’s very dependent on team and org culture.**