[[ReadItLater]] [[Article]]

# [Why Scrum Fails | Better Programming](https://betterprogramming.pub/why-scrum-fails-ac92cab05c6a)

## Why is it that we all follow a process called “Scrum,” and yet no one actually follows the process that the Scrum Guide defines as Scrum?


This [ubiquitous](https://www.professionaldevelopment.ie/who-uses-scrum) thing called “Scrum” is an [oppressive](https://ronjeffries.com/articles/016-09ff/defense/) tool for [micromanagement](https://age-of-product.com/agile-micromanagement/). [It’s all about story points and velocity](https://youtu.be/DmJXpI7OJuY?t=510). It has earned the utter contempt of [developers](https://youtu.be/HURvJDldVGA), [designers](https://www.kovacevic.io/ux-designers-hate-scrum-for-a-reason.html), [product managers](https://betterprogramming.pub/is-agile-impoverishing-product-culture-ff37dfeffea3), and [middle managers](https://www.forbes.com/sites/stevedenning/2015/01/26/why-do-managers-hate-agile/?sh=1fa6fb893a57) alike. The maddening thing about it is that there are well-known solutions to all of these problems, and they can be found in a concise, 14-page document called the [Scrum Guide](https://scrumguides.org/).

The Guide is pretty clear about what is and isn’t Scrum:

> The Scrum framework, as outlined herein, is immutable. While implementing only parts of Scrum is possible, the result is not Scrum.

Very few of us have ever actually worked on a Scrum team (as the Scrum Guide defines it), but there’s no shortage of us who’ve worked in [Scrum cargo cults](https://medium.com/@jason.godesky/the-scrum-cargo-cult-98def5b4af2f).

There is no virtue in following Scrum in and of itself. *Agility* is important, but Scrum is just one way to achieve that. But almost everyone who “adopts Scrum” removes crucial elements that make it work before they begin even a single sprint. This isn’t about a religious devotion to the chapter and verse of the Scrum Guide, but simply understanding how it works. That’s why we use the metaphor of a cargo cult, because we end up mimicking the outward appearance of the system while removing the vital pieces that would make it work.

This raises a deeper question, then: why is it that we all follow a process called Scrum, and yet no one actually follows the process that the Scrum Guide defines as Scrum?

There are many problems that arise in agile transformations, but I find two passages from the Scrum Guide that come up particularly often:

> Scrum Teams are cross-functional, meaning the members have all the skills necessary to create value each Sprint. They are also self-managing, meaning they internally decide who does what, when, and how.

and:

> The entire Scrum Team is accountable for creating a valuable, useful Increment every Sprint.

## The Increment

Though separated awkwardly in the excerpts above, the second passage and the first sentence of the first passage go together.

-   *Scrum Teams are cross-functional, meaning the members have all the skills necessary to create value each Sprint.*
-   *The entire Scrum Team is accountable for creating a valuable, useful Increment every Sprint.*

You need a cross-functional team in order to create a valuable, useful increment every sprint. If teams are broken down by function, then you need the UX team to work ahead of the development team ([as Nielsen Norman Group recommends](https://www.nngroup.com/articles/ux-agile-backlog/)), but that means that the UX team isn’t releasing an increment each sprint: they’re just producing backlog items for the development team. That’s probably making it difficult for the development team to produce a valuable, useful increment, too. If we can’t use [working software](https://agilemanifesto.org/principles.html) as the primary measure of progress, then what choice do we have but to rely on [estimates](https://medium.com/@jason.godesky/all-software-estimates-are-lies-d5847a080ef9)? This is how Scrum becomes focused on story points and velocity instead of customers and value. But as [the very first principle](https://agilemanifesto.org/principles.html) of the [Manifesto for Agile Software Development](https://agilemanifesto.org/) plainly states:

> Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.

Meaning that if you’re not continuously delivering valuable software to customers, whatever you’re doing isn’t agile. A Scrum team that doesn’t deliver a valuable, useful increment every sprint isn’t a Scrum team. In his essay on “[Dark Scrum](https://ronjeffries.com/articles/016-09ff/defense/)” (already linked above), [Ron Jeffries](https://ronjeffries.com/) (yes, the same Ron Jeffries whose name you will find affixed to the aforementioned Manifesto) points out the critical role that the increment plays, and how much of the oppressive “Scrum” we’ve all come to know and loathe arises from the lack of it.

> …the more true and real our product increment is, the more it will influence people to look at reality and base their management on it. Contrary to what we often think, our leaders are not stupid. They’re doing the best they can with the information they have. If we can give them better information, in the form of working software, they’ll begin to use that information. Using that information, they’ll resort to less pressure and less abuse.

There are reasons we don’t do this. One is an organizational problem: we’re siloed into functional teams, making it logistically (or perhaps politically) difficult, if not impossible, to form cross-functional teams. Another reason is that [carving a big project into vertical slices is genuinely difficult to do](https://medium.com/@jason.godesky/the-art-of-the-vertical-slice-e9a9c9c63642). A third is that even when we do that, as Ron Jeffries also writes in that same essay:

> …the increment must actually work. It really has to be tested, integrated, ready to ship, containing all the backlog items we’ve undertaken to do.

This is the part where Scrum challenges the normal way of doing things, so rather than change the way we do things, we tell ourselves that we’re an exception; that this might work elsewhere, but it can’t really work for us, so we’ll have to make a compromise with reality. This is almost never true, of course. We assume that the organizations that have done it did so because it was easier for them, rather than facing the fact that it was just as difficult for them, but they did it anyway to achieve the goals they desired.

It’s true that the Scrum Guide doesn’t go into detail about why the increment matters; it just tells you that you need to follow everything in the guide, and some of it is quite terse. This is one of the most important points in the framework, the beating heart that makes the whole thing work, but it would be easy to miss that from a casual read. To make a concise 14-page document, the Scrum Guide expects readers to take it seriously and find out why and how it all fits together from using it a few times, but since it’s so rare for organizations to form cross-functional teams and expect a working increment at the end of each sprint, few ever experience how or why it all works.

## The Self-Managing Team

We sometimes hear about the importance of self-management when it comes to staying late to fix bugs or taking responsibility for server outages or downtime, but how often do Scrum teams decide that they’re going to develop fewer new features this sprint so that they can focus on writing more unit tests? Or to pay off some of their mounting technical debt? How often do Scrum teams make the decision to hire a new member to the team? Or to remove someone from it?

One of the biggest questions in many agile transformations is where managers fit into Scrum. Are they the Scrum Masters? The product owners? The Scrum Guide is actually quite clear on this:

> \[Scrum Teams\] are also self-managing, meaning they internally decide who does what, when, and how.

[Allen Holub](https://holub.com/) is my favorite [critic of Scrum](https://youtu.be/WFbvJ0dVlHk). He has written and talked about this precise subject quite a bit, and why it so often leads to the failure of Scrum. Managers can see that agility is an existential threat to them, so they naturally band together to sabotage it. Sometimes this is conscious, but just as often (if not more often) it’s benign. They’re looking for where they fit into the new order, and they adjust the process to make room for themselves. They can even convince themselves that they’re taking responsibilities off of the developers’ shoulders so they can focus more on the work. As [Mike Cohn wrote](https://www.mountaingoatsoftware.com/blog/ssssh....agile-is-all-about-micromanaging#author), though:

> …agile is about micromanagement, but it’s about the team micromanaging themselves and for their own benefit.

So as helpful as managers may hope to be, by taking the management tasks off their teams’ shoulders, they’re taking away their autonomy and turning the process into an oppressive instrument of control.

Allen Holub stresses that if an agile transformation means that management will all be out of a job, then we ensure that transformation’s failure. To succeed, a transformation needs to provide a future for all the people whose current roles would be eliminated by it. He says that in a humane company, they’d look for ways that managers could become Scrum Masters or product owners or team members, according to where their skills and interests lie. If that means new training, that can be provided. And if they don’t want to be part of the new, agile future, the company should keep them on, with pay and benefits, while it helps them find a new position somewhere else that will suit them better.

Without such humane treatment, management becomes an entrenched obstacle to agility, fighting against our efforts for their own survival. A transformation that creates factions within the organization and pits them against one another is unlikely to succeed — especially when the faction most pitted against it is the one that makes all the decisions.

[David Marquet](https://youtu.be/OqmdLcyES_Q) has championed the “leader-leader” approach to leadership with the principle that decisions should be made, as much as possible, by the people who know the most about the matter at hand. That will almost always be the people who do the work, not a manager or an executive. Scrum moves organizations to this kind of leadership by defining a Scrum team as self-managing. Delivering a valuable, useful increment each sprint is a significant responsibility. We cannot expect Scrum teams to uphold that responsibility if we don’t empower them to make the decisions necessary to do so. You can’t be agile, because there’s a command and control apparatus that you need to go through to approve your decisions, which is an added delay, making the loop of inspection and adaptation take longer. If there’s someone managing your work, then you’re not part of a self-managing team — so whatever else your team is, according to the Scrum Guide, it’s not a Scrum team.

## The Monkey’s Paw Problem of Scrum

According to [a survey](https://www.parabol.co/resources/agile-statistics/#agile-transformation) published by [Parabol](https://www.parabol.co/), the top reasons businesses try to increase agility are:

1.  faster delivery to customers (83%)
2.  improving productivity (76%)
3.  increasing predictability, transparency, and visibility (70%)
4.  improving efficiency (69%)
5.  improving work organization methods (68%)

#1, #2, and #4 are all closely related — almost but not quite synonymous. Rethinking how we work together does make it into the top five, but only just. In that gap, we can see the assumption that the business is doing just fine — we just need those developers to get more done.

Scrum is seen primarily in those terms: as a means of increasing output, and as something that’s relevant to the software development team alone. If software development requires a Scrum Master, then the manager can do that; if it requires a Product Owner, then a project manager can do that. We can map all of our existing roles and processes to Scrum terms easily enough. We can set up Jira instances and schedule sprint reviews and daily stand-ups. None of that poses any great obstacle to the way we’ve always done things. But a cross-functional team would mean disrupting the departmental divisions that the company has formed (and possibly the reporting hierarchy formed around those divisions). Self-managing teams could jeopardize all of the organization’s managers as a group. Suggestions like those go beyond the purview of the agile transformation — because the real goal isn’t to transform the organization into a more agile one, but to transform the development team into a team that produces more output.

This is why organizations are often impatient with the turbulent early stages of an agile transformation (the “storming” and early “norming” stages in the [Tuckman model](https://en.wikipedia.org/wiki/Tuckman%27s_stages_of_group_development)), when the disruption of a new change slows down work. This is when many organizations intervene to impose changes to Scrum, to make it “more accountable” or “adapt” it to “better fit” their work. This often means a greater focus on story points, velocity, and other metrics so that the business can ensure that the team is maintaining output levels. [Goodhart’s law](https://en.wikipedia.org/wiki/Goodhart%27s_law) goes into effect, as the team becomes adept at producing the metrics that they’re responsible for, even if they don’t produce any more working software than they ever did before.

Scrum fails for the exact same reason that it’s ubiquitous. It’s garnered a reputation as a quick and relatively painless way for organization to increase the output of their development teams. But because it’s seen as a quick and relatively painless way to increase the output of a development team, organizations often resist suggestions that it should involve more than just the development team, or for changes that aren’t quick or painless, or if it means accepting a drop in output (even temporarily). You’ll note that those two critical parts of the Scrum Guide that we discussed as being frequently ignored by organizations are precisely the parts of Scrum that go beyond the development team and ask the organization to genuinely transform. To quote Allen Holub once again:

## Agility Beyond Scrum

I hope the [Scrum Alliance](https://www.scrumalliance.org/) doesn’t take away my certification for saying this out loud, but I think Scrum may have outlived its usefulness. The heart of Scrum is its cycle of inspection and adaptation. As I keep paraphrasing [Dave Thomas](https://pragdave.me/), the basic algorithm of agility is:

1.  Figure out where you are.
2.  Take a small step towards your goal.
3.  Adjust your understanding based on what you learned.
4.  Go to step 1.

The Scrum that’s described in the Scrum Guide does that, but it’s been marketed as a panacea in such a way that businesses ignore critical parts of what makes it work. As [Tim “Agile Otter” Ottinger](https://www.industriallogic.com/people/tottinge/) [pointed out](https://www.industriallogic.com/blog/faster-and-more-predictable/):

> The problem begins with a simple realization that nearly all software development policies and processes exist *to prevent software from being released*.

So when organizations decide which parts of Scrum to take or leave, they do so with a bias towards the processes they know and understand —processes that are all about preventing software from being released. Which makes it much more difficult to execute step 2 of our algorithm, which lengthens the cycles, which ultimately gnaws at the whole purpose of the exercise.

When it was developed in the 1990s, putting valuable, useful software into the hands of customers every two weeks was a radical idea. Scrum was offering the quickest cycle of inspection and adaptation around. Today, though, continuous delivery means that we routinely put valuable, useful software into the hands of our customers several times a day.

Continuous delivery makes Scrum obsolete. Agility — as in the approach to work that you’ll be led to if you take seriously the values and principles in the [Manifesto for Agile Software Development](https://agilemanifesto.org/) — remains as important as it’s ever been. Scrum *could* have been an incredible force for good; sadly, instead it became yet another tool for oppression and abuse. The solutions to those problems still exist — in the Scrum Guide itself, tragically enough— but at this point, is there really any hope of rescuing Scrum from the Agile Industrial Complex?

So maybe it’s time to explore agility beyond Scrum. Continuous delivery takes its name from that previously-quoted first principle from the Manifesto, taking that premise to a degree that might have seemed impossible back in 2001. It allows us to take even smaller steps — small enough to execute Dave’s algorithm several times a day.

In [the same article I cited above](https://www.industriallogic.com/blog/faster-and-more-predictable/), Tim Ottinger suggests that a way to get around the loops, queues, and delays built into our usual processes for delivering software (without sacrificing our standards of quality) is to…

> …gather the people who would have handed off the work between them and have them work on one work item together, reviewing and testing on-the-fly. That includes developers, testers, UX, UI, security, … all the people.

One of the most important things to keep from Scrum is the one thing almost all of us were cutting out before we ever tried it: the autonomous, self-managing, cross-functional team. In fact, we need to take it even further. It’s not enough just to assemble such a team; we also need to make mob development the norm for them. This is a technique that complements continuous delivery exceptionally well.

There is only one practice prescribed by the Manifesto, though. It’s the final principle:

> At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

You don’t need a framework to become agile. You need a team that’s committed to becoming more agile, you need an organization that’s open to trying new things, and you need a regularly-scheduled retrospective. If you have that, then a good retrospective will produce all of the other processes and practices that you need, creating a particular approach to agility that’s tailor-made for the work that you do.