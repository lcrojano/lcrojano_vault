[[ReadItLater]] [[Article]]

# [How Google takes the pain out of code reviews, with 97% dev satisfaction](https://engineercodex.substack.com/p/how-google-takes-the-pain-out-of)

*Engineer’s Codex is a publication about real-world software engineering.*

A lot of ex-Google engineers talk about how much they miss **Critique, Google’s code review tool,** out of all the internal tools they leave behind.

Another Reddit comment laments about how they [“miss \[Critique\] so bad”](https://www.reddit.com/r/programming/comments/18ae0gc/comment/kbxjg6b/?utm_source=share&utm_medium=web2x&context=3), listing off various features they miss, like its “attention set,” which is explained below.

This tracks with Google’s own findings. Internally, **97% of Google software engineers are satisfied with Critique.[1](https://engineercodex.substack.com/p/how-google-takes-the-pain-out-of#footnote-1-139414745)**

But what is Critique exactly and what makes it so good? 

How does this pair with Google’s actual process of code review?

In this article, I dive into:

-   Google’s guidelines for efficient code review
    
-   Critique, their code review tooling, and AI-powered improvements
    
-   Internal statistics on Google code reviews
    
-   Why Critique seems to be so loved by Googlers
    

While the [SWE Book](https://abseil.io/resources/swe-book/html/toc.html) covers the basics of Critique, new [blog posts](https://blog.research.google/2023/05/resolving-code-review-comments-with-ml.html) and [research](https://research.google/pubs/?area=software-engineering) by Google show new developments in their code review processes, such as using AI to make automatic suggestions and improvements to code changes.

To understand how Google writes clean, maintainable code, I wrote about [Google’s readability process here](https://engineercodex.substack.com/p/how-google-writes-clean-maintainable).

Google’s [guidelines for a good code review](https://google.github.io/eng-practices/review/reviewer/standard.html) include:

-   **Continuous improvement over perfection:** While a more seasoned developer may find a less experienced developer’s code to not be up to their personal standard, Google encourages continuous improvement over perfection. Developers need to make progress; overly difficult reviews can discourage future improvements. 
    
-   **Maintain or improve the health of the codebase**
    
-   **Follow the Style Guide:** When code style comes into question, [Google’s style guides](https://google.github.io/styleguide/) are followed and referenced to a tee.
    
-   **Always Share Knowledge:** Reviewers are encouraged to share knowledge about language features, the codebase, and other relevant artifacts through code review. Usually, these guidelines are sent with “supporting documentation,” such as links to [Google/Abseil’s C++ Tips of the Week](https://abseil.io/tips/). 
    
    -   At Google, the educational aspects of a code review are highly emphasized.
        
-   **Write Small Changes**: Keep changes limited to about 200 lines of code if possible.
    
-   **Strict Standards for Lightweightness**: Google expects reviewers to review a code change in less than 24 hours and encourages reviews to only have one reviewer if possible, which saves time for everyone involved.
    
    -   *“The majority of changes at Google are small, have one reviewer and no comments other than the authorization to commit. During the week, 70% of changes are committed less than 24 hours after they are mailed out for an initial review.”*[2](https://engineercodex.substack.com/p/how-google-takes-the-pain-out-of#footnote-2-139414745)
        
-   **Politeness and Professionalism**: Maintaining a culture of trust and respect is crucial. Feedback should be professional, avoiding personal criticism. Reviewers should be open to the author's approach, offering alternatives only if necessary, and treating each comment as a learning opportunity.
    
    -   I wanted to comment on this one specifically, as while it seems obvious, it’s not as easy to do in practice. It’s common for people to get attached to the code they’ve written or for reviewers to come off as harsher than they meant to. The written word leads for less nuanced communication compared to face-to-face.
        
    -   Google has done a lot of research into how code comments can affect developer productivity and motivation.
        
        -   [Predicting Developers’ Negative Feelings about Code Review](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/7ac08fa960dfe10561c1f5953419a0c945279faa.pdf)
            
        -   [Destructive Criticism in Software Code Review Impacts Inclusion](https://research.google/pubs/pub51232/)
            
        -   [Detecting Interpersonal Conflict in Issues and Code Review: Cross Pollinating Open- and Closed-Source Approaches](https://research.google/pubs/pub51204/) 
            
        -   [Using research to make code review more equitable](https://developers.googleblog.com/2022/06/Using-research-to-make-code-review-more-equitable.html)
            

For a changelist ([CLs are Google’s version of pull requests](https://news.ycombinator.com/item?id=20891103), or PRs) to go through, it must have 0 unresolved comments, a LGTM (Looks Good To Me) from at least one reviewer, and 2 types of approval:

-   people who “own” the part of the codebase the files go into
    
-   [Readability](https://engineercodex.substack.com/p/how-google-writes-clean-maintainable) approvals, who approve the “readability” and style of the code
    

One person can be the LGTM-er and approver all at once.

Critique is Google’s code review tool, allowing engineers to efficiently review and submit code changes.

They also have a diff view between the current codebase and the proposed changes:

Importantly, Google’s [recent publications](https://blog.research.google/2023/05/resolving-code-review-comments-with-ml.html) in 2023 show they have comprehensive **AI-powered code review tools in-house now** (as shown above). 

**When reviewers leave comments on code, Critique will show suggested ML-powered edits, which mean that the author of the code review just has to click one button to address the comment in entirety.**

Recent developments, based on Google research papers, tell us that Google is improving developer productivity with AI-powered code review tools where possible.

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fafef4989-ac0c-4cb8-a2c2-6a583d82c52e_899x302.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fafef4989-ac0c-4cb8-a2c2-6a583d82c52e_899x302.png)

The [SWE Book](https://abseil.io/resources/swe-book/html/ch19.html) covers Critique in detail with over 5000 words, but I summarize the key points here and have provided a link for those who want to dive deeper into it. 

A CL (or Pull Request) is created in [Google’s in-house code editor Cider](https://news.ycombinator.com/item?id=13076417), which is “tightly integrated with Critique and other in-house Google tools”, leading to higher developer productivity.

-   **Prereview Tools:** Critique assists in polishing changes before review, showing diffs, build and test results, and style checks.
    
-   **Diffing and Visualization:** Enhanced with syntax highlighting, cross-references, intraline diffing, whitespace ignoring, and move detection.
    
-   **Analysis Results:** Displays results from [static analyzers](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/3198e114c4b70702b27e6d88de2c92734c9ac4c0.pdf), highlighting important findings and offering fix suggestions. These include “presubmits,” which are automated tests that are run in Critique that enforce project-specific invariants.
    

> Critique integrates feedback channels for analysis writers.
> 
> Reviewers have the option to click “Please fix” on an analysis generated comment as a signal that the author should fix the issue.
> 
> Either authors or reviewers can click “Not useful” in order to flag an analysis result that is not helpful in the review process. ([Source](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/3198e114c4b70702b27e6d88de2c92734c9ac4c0.pdf))

When a pull request is ready to be reviewed, the code author adds reviewers and sends it to them officially for review.

When a PR/CL is sent in for review, “presubmits” are run if they haven’t already on the current snapshot of code. This means that everyone involved in the review knows whether or not the code breaks anything.

Code reviews can also be [anonymized](https://research.google/pubs/pub50130/), where the code author can be kept anonymous from the reviewer. However, Google didn’t find much of an useful difference between anonymous code reviews and “real” code reviews.[3](https://engineercodex.substack.com/p/how-google-takes-the-pain-out-of#footnote-3-139414745)

-   Anyone can comment on a change and there are features to track review progress and resolve comments.
    
    -   *Unresolved comments* represent action items for the change author to definitely address. These can be marked as “resolved” by the code author themselves when they reply to the comment.
        
    -   *Resolved comments* include optional or informational comments that may not require any action by a change author
        

There’s a dashboard for review statuses and an “**attention set”** which lets people involved in a certain code review who is the current person being waited upon.

> *The attention set is commonly a highly-regarded feature by Google engineers.*

As noted above, for a review to go in, it needs an LGTM from at least one reviewer. It needs 0 unresolved comments, though a code author can mark a comment resolved themselves when they reply. It also needs approvals from owners of the part of the codebase the code is going into, along with a [readability approval](https://engineercodex.substack.com/p/how-google-writes-clean-maintainable).

As mentioned before, this can all be done by one reviewer.

Changes are submitted and committed within Critique itself.

Critique is valuable even after changes are submitted.

> *“Google researchers found strong evidence that Critique’s uses extend beyond reviewing code. Change authors use Critique to examine diffs and browse analysis tool results. In some cases, code review is part of the development process of a change: a reviewer may send out an unfinished change in order to decide how to finish the implementation. Moreover, developers also use Critique to examine the history of submitted changes long after those changes have been approved.”*

Google conducted [a study on code review at the company specifically](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/80735342aebcbfc8af4878373f842c25323cb985.pdf). I’ve listed some interesting stats from their paper.

**Change Authoring Frequency**:

-   Median: 3 changes per week.
    
-   80% of authors make fewer than 7 changes weekly.
    

**Review Frequency**:

-   Median: 4 changes reviewed per week.
    
-   80% of reviewers handle fewer than 10 changes weekly.
    

**Time Spent Reviewing Per Week:**

-   Average: 3.2 hours per week
    
-   Median: 2.6 hours per week
    

**Initial Feedback Waiting Time**:

-   Small changes: Median time under 1 hour.
    
-   Very large changes: About 5 hours.
    

**Overall Review Process Time**:

-   Median latency for all code sizes: Under 4 hours.
    
-   **Comparison with Other Companies**:
    
    -   AMD: 17.5 hours (median time to approval).
        
    -   Chrome OS: 15.7 hours.
        
    -   Microsoft Projects: 14.7, 19.8, and 18.9 hours.
        
    -   Microsoft (another study): 24 hours.
        

> *“Previous studies have found that the number of useful comments decreases and the review latency increases as the size of the change increases. Size also influences developers’ perception of the code review process; a survey of Mozilla contributors found that developers feel that size-related factors have the greatest effect on review latency.” ([Source](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/80735342aebcbfc8af4878373f842c25323cb985.pdf))*

Furthermore, the number of comments received per change decreases with seniority.

Most Googlers and ex-Googlers are big fans of Critique.

Internally, **97% of Google software engineers are satisfied with Critique.**[4](https://engineercodex.substack.com/p/how-google-takes-the-pain-out-of#footnote-4-139414745)

I asked 7 Googlers about why they prefer Critique over tools they may have used in the past, like GitHub.

They noted:

-   **Static analysis:** Google has a full-featured suite of [static analysis tools](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/3198e114c4b70702b27e6d88de2c92734c9ac4c0.pdf) that provide actionable feedback on code automatically. This saves both code authors and reviewers time as reviewers then don’t have to nitpick at obvious items.
    

-   **Focus on only the latest changed files**: There’s a focus on just the latest “snapshot” of code. Previous snapshots, commits, and code changes are not really a focus, allowing for a cleaner user interface.
    
-   **A familiar, side-by-side diffing interface:** It shows "diff from the last review" by default.
    
-   **ML-powered suggestions:** Google’s new ML-powered suggestions speed up code review immensely.
    
-   **Tight integration with other Google tooling:** Critique is integrated extremely well with Google’s IDE and other internal tools, like their bug tracker. When everything is connected together, productivity is better.
    
    -   This includes easy linking of code, comments, and tickets.
        
-   **“Action set” tracking**: This lets people know who is supposed to be taking the next action.
    
-   **Satisfying gamification**: While Critique isn’t built to be gamified, Googlers reported how they enjoyed it when Critique “went green,” which meant a PR was ready to submit (all tests passed, reviewers LGTM-ed and approved).
    

[A Reddit comment lists more](https://www.reddit.com/r/programming/comments/18ae0gc/comment/kbxjg6b/?utm_source=share&utm_medium=web2x&context=3):

[

![](_Inbox/Read%20Later/assets/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F56798bd6-1d0c-4110-8fb4-c3030f1e2c1a_1456x1082.png)

](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F56798bd6-1d0c-4110-8fb4-c3030f1e2c1a_1456x1082.png)

[A great quote on static analysis](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/3198e114c4b70702b27e6d88de2c92734c9ac4c0.pdf):

> A qualitative study of 88 Mozilla developers found that static analysis integration was the most commonly-requested feature for code review.
> 
> Automated analyses allow reviewers to focus on the understandability and maintainability of changes, instead of getting distracted by trivial comments (e.g., about formatting).

**While many of these features are available in other tools today, I believe it is the tight integration and extreme “personalization” of the tooling towards a Google-specific workflow and codebase that makes it so loved.**

At the same time, that means it’s not realistic for every company to replicate Critique and related tools exactly. For example, some of their tooling seems specific to challenges created by their monorepo structure.

While Critique itself will never be open-sourced, [Gerrit](https://www.gerritcodereview.com/) is a similar tool to Critique. It’s an open-source code review tool also created and maintained by Google.

However, I think Google does put a lot of effort and thought into developer productivity. They [publish their research freely](https://research.google/pubs/?area=software-engineering) and there are useful takeaways from their work.