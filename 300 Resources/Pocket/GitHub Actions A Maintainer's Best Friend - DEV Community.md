---
url: https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n
readlater:
  id: "3958407392"
  provider: pocket
  synchtime: 1699293687228
---
[![Cover image for GitHub Actions: A Maintainer's Best Friend](https://res.cloudinary.com/practicaldev/image/fetch/s---uoHKjGg--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/escjy67qg8keb9i45wmw.png)](https://res.cloudinary.com/practicaldev/image/fetch/s---uoHKjGg--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/escjy67qg8keb9i45wmw.png)

[![OpenSauced profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--vegTPF21--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/organization/profile_image/2498/a16cc27c-33f9-40b6-92a8-4a43f70a96ef.png)](/opensauced) [![Nick Taylor](https://res.cloudinary.com/practicaldev/image/fetch/s--EkBIkzdc--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)](/nickytonline)

[Nick Taylor](/nickytonline) for [OpenSauced](/opensauced)

Posted on Oct 31

   ![](https://dev.to/assets/sparkle-heart-5f9bee3767e18deb1bb725290cb151c25234768a0e9a2bd39370c382d02920cf.svg)  ![](https://dev.to/assets/multi-unicorn-b44d6f8c23cdd00964192bedc38af3e82463978aa611b4365bd33a0f1f4f3e97.svg)  ![](https://dev.to/assets/exploding-head-daceb38d627e6ae9b730f36a1e390fca556a4289d5a41abb2c35068ad3e2c4b5.svg)  ![](https://dev.to/assets/raised-hands-74b2099fd66a39f2d7eed9305ee0f4553df0eb7b4f11b01b6b1b499973048fe5.svg) ![](https://dev.to/assets/fire-f60e7a582391810302117f987b22a8ef04a2fe0df7e3258a5f49332df1cec71e.svg)

# GitHub Actions: A Maintainer's Best Friend

[#githubactions](/t/githubactions) [#automation](/t/automation) [#opensource](/t/opensource) [#productivity](/t/productivity)

## [Maintainer Toolkit (2 Part Series)](/nickytonline/series/24726)

[1 Supercharge your Repository with Code Owners](/opensauced/supercharge-your-repository-with-code-owners-4clg "Published Sep 21") [2 GitHub Actions: A Maintainer's Best Friend](/opensauced/github-actions-a-maintainers-best-friend-488n "Published Oct 31")

As developers, it’s in our best interest to automate things. The less we have to do in a manual way, the better. As soon as manual intervention is required, there is potential for failure or a mishap. Aside from that, it’s your time as a maintainer that could be spent elsewhere.

If you host your code on GitHub, besides scripts to automate certain actions, you can also leverage the huge ecosystem of [GitHub  
Actions](https://github.com/features/actions).

## [](#practical-examples)Practical Examples

Let’s look at some practical examples of GitHub actions helping maintainers.

### [](#peterevanscreateorupdatecomment)peter-evans/create-or-update-comment

If someone opens an issue on your repository, you could respond with a personal message saying thank you, but those keystrokes are probably better suited for other things. Automate a message reply instead, thanking the community member for creating the issue and mentioning you will look into it. An automated message to the issue opener is friendly, even if it’s automated.

A great GitHub action for this is Peter Evans’ [Create or Update Comment](https://github.com/peter-evans/create-or-update-comment) action.

It’s used in the app repository for OpenSauced. Here’s [how we have it configured](https://github.com/open-sauced/app/blob/beta/.github/workflows/issue.yml).

When a new issue is opened, an issue responds with the following:

[![Automated comment when an issue is created in the OpenSauced App repository that says "Thanks for the issue, our team will look into it as soon as possible! If you would like to work on this issue, please wait for us to decide if it's ready. The issue will be ready to work on once we remove the "needs triage" label. To claim an issue that does not have the "needs triage" label, please leave a comment that says ".take". If you have any questions, please reach out to us on Discord or follow up on the issue itself. For full info on how to contribute, please check out our contributors guide."](https://res.cloudinary.com/practicaldev/image/fetch/s--ydQcc7b2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y9zucj40s8ub6jiacrl3.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--ydQcc7b2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y9zucj40s8ub6jiacrl3.png)

### [](#bdougietakeaction)bdougie/take-action

My coworker bdougie ([@bdougieyo](https://dev.to/bdougieyo)) created the [take Github action](https://github.com/bdougie/take-action). It allows external contributors to self-assign issues by typing `.take` into a comment of an issue. This removes the burden of a bit of back and forth between contributors and maintainers.

[![OpenSauced contributor itskish0re self assigning an issue by using the .take command](https://res.cloudinary.com/practicaldev/image/fetch/s--xnS_7glM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eh9gjzo8aiwleqqr7qhe.png)](https://github.com/open-sauced/app/issues/2017#issuecomment-1785492904)

Of course, we don’t want external contributors self-assigning any issue they want. The take action also has the concept of blocking labels. For example, if an issue has a `👀 needs triage` label, we can add this label to a list of blocking labels.

[![Someone trying to self-assign an issue when there are blocking labels on the issue](https://res.cloudinary.com/practicaldev/image/fetch/s--9zgUaax6--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w52j0puh47kpgg27clnd.png)](https://github.com/open-sauced/app/issues/1952#issuecomment-1772176129)

### [](#balazsorban44nissuer)balazsorban44/nissuer

Another action that came onto my radar a couple of days ago was thanks to [styfle](https://twitter.com/styfle). Although I haven’t used it yet, [nissuer](https://github.com/balazsorban44/nissuer) looks like a great utility belt GitHub action for maintainers. The Next.js repository uses it, so I'm sure it brings lots of value to a maintainer.

I love this note they added in the README.

> NOTE: Developers are coming to your project with all sorts of backgrounds/skill levels or understanding of the open-source world. Show empathy while using this action. 💚 We recommend adding comments that not only dismiss unhelpful issues/comments, but educate the user on how to be more helpful in the future.

### [](#bespoke-actions)Bespoke Actions

Don’t see a GitHub action for what you need? Create your own. You can even build your own by composing it from existing GitHub actions. Here's an example of a [bespoke workflow I use for pulling in my latest video content from YouTube](https://github.com/nickytonline/www.nickyt.co/blob/main/.github/workflows/get-latest-videos.yml) to my blog.

I'm using some GitHub Actions, a custom script that leverages the [GitHub CLI](https://cli.github.com/) and magic.  

```
name: Get latest videos
on:
  schedule:
    # Everyday at midnight UTC
    - cron: '0 0 * * *'
  workflow_dispatch:

jobs:
  update_profile_data:
    name: Get latest videos
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - name: Get latest videos
        run: |
          npm install
          node bin/udpdateStreamingPage.js
      - name: Setup git config
        run: |
          git config user.name 'token-generator-app[bot]'
          git config user.email '82042599+token-generator-app[bot]@users.noreply.github.com'
      - name: PR for Videos
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: |
          ./bin/pr-videos.sh
```

 

You can see the results on the [streaming page of my site](https://www.nickyt.co/pages/streaming/).

The post is a bit out of date, but I discuss more in depth the automations for my website in

[

![nickytonline](https://res.cloudinary.com/practicaldev/image/fetch/s--f49_KtT1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://res.cloudinary.com/practicaldev/image/fetch/s--oY_gN94h--/c_fill%2Cf_auto%2Cfl_progressive%2Ch_150%2Cq_auto%2Cw_150/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)

](/nickytonline)[

## Automate syndication of your content with Eleventy, dev.to, and GitHub Actions

### Nick Taylor ・ May 26 '22

#eleventy #githubactions #node #webdev



](/nickytonline/my-eleventy-meetup-talk-3b2p)

## [](#conclusion)Conclusion

These are just examples of tasks you can automate, and if you’re using GitHub, there is a huge ecosystem of GitHub actions to help with your automation goals.

What are some GitHub actions that you’ve leveraged in your projects? Share them in the comments.

Stay saucy friends!

## [Maintainer Toolkit (2 Part Series)](/nickytonline/series/24726)

[1 Supercharge your Repository with Code Owners](/opensauced/supercharge-your-repository-with-code-owners-4clg "Published Sep 21") [2 GitHub Actions: A Maintainer's Best Friend](/opensauced/github-actions-a-maintainers-best-friend-488n "Published Oct 31")

## Top comments (4)

### Sort discussion:

- [
    
     Top
    
    Most upvoted and relevant comments will be first
    
    ](/opensauced/github-actions-a-maintainers-best-friend-488n?comments_sort=top#toggle-comments-sort-dropdown)
- [
    
    Latest
    
    Most recent comments will be first
    
    ](/opensauced/github-actions-a-maintainers-best-friend-488n?comments_sort=latest#toggle-comments-sort-dropdown)
- [
    
    Oldest
    
    The oldest comments will be first
    
    ](/opensauced/github-actions-a-maintainers-best-friend-488n?comments_sort=oldest#toggle-comments-sort-dropdown)

Subscribe

    ![pic](https://res.cloudinary.com/practicaldev/image/fetch/s--V3djhsWJ--/c_limit,f_auto,fl_progressive,q_auto,w_256/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8j7kvp660rqzt99zui8e.png)

Personal Trusted User

[Create template](/settings/response-templates)

Templates let you quickly answer FAQs or store snippets for re-use.

Submit Preview [Dismiss](/404.html)

 

 

[![thomasbnt profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--EQW3U89X--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/18254/c3e65d32-bfe2-48ed-93b3-f2caf9c60dd7.png)](https://dev.to/thomasbnt)

[Thomas Bnt](https://dev.to/thomasbnt)

Thomas Bnt

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--Iv24f4-g--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/18254/c3e65d32-bfe2-48ed-93b3-f2caf9c60dd7.png)Thomas Bnt](/thomasbnt)

Follow

French web developer mainly but touches everything. Volunteer mod here at DEV. I learn Nuxt at this moment and databases. — Addict to Cappuccino and Music

- Location
    
    France
    
- Pronouns
    
    He/him
    
- Work
    
    Freelancer at ConceptWeb.agency
    
- Joined
    
    May 5, 2017
    

• [Oct 31](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2adf8)

- [Copy link](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2adf8)

- Hide

GA is really useful, thanks for your post ! 👻

2 likes Like [ Reply](#/opensauced/github-actions-a-maintainers-best-friend-488n/comments/new/2adf8)

 

 

[![nickytonline profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--EkBIkzdc--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)](https://dev.to/nickytonline)

[Nick Taylor](https://dev.to/nickytonline)

Nick Taylor

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--h-JUieId--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)Nick Taylor](/nickytonline)

Follow

- Email
    
    [nick@nickyt.co](mailto:nick@nickyt.co)
    
- Location
    
    Montréal, Québec, Canada
    
- Education
    
    University of New Brunswick
    
- Joined
    
    Mar 11, 2017
    

• [Oct 31](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2adfl)

- [Copy link](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2adfl)

- Hide

[![Captain America saluting](https://i.giphy.com/media/kRkJXYahXjSE0/giphy.gif)](https://i.giphy.com/media/kRkJXYahXjSE0/giphy.gif)

2 likes Like [ Reply](#/opensauced/github-actions-a-maintainers-best-friend-488n/comments/new/2adfl)

 

 

[![raskyld profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--PrOGEPC4--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1190909/99f86728-581c-4da3-98d5-d2011787485c.png)](https://dev.to/raskyld)

[Enzo Nocera](https://dev.to/raskyld)

Enzo Nocera

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--GfyEI8AS--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/1190909/99f86728-581c-4da3-98d5-d2011787485c.png)Enzo Nocera](/raskyld)

Follow

Just a Platform Engineer working in the dark empowering Developers to let them shine.

- Location
    
    Lille, France
    
- Work
    
    Platform Engineer at Scaleway
    
- Joined
    
    Oct 21, 2023
    

• [Nov 1](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2ae2m)

- [Copy link](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2ae2m)

- Hide

I didn't except such useful posts when I first followed _OpenSauced_, but your contents are truly awesome! 🙏

2 likes Like [ Reply](#/opensauced/github-actions-a-maintainers-best-friend-488n/comments/new/2ae2m)

 

 

[![nickytonline profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--EkBIkzdc--/c_fill,f_auto,fl_progressive,h_50,q_auto,w_50/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)](https://dev.to/nickytonline)

[Nick Taylor](https://dev.to/nickytonline)

Nick Taylor

 [![](https://res.cloudinary.com/practicaldev/image/fetch/s--h-JUieId--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/9597/2629be65-f045-4612-a7e9-28cd9e48bd49.jpg)Nick Taylor](/nickytonline)

Follow

- Email
    
    [nick@nickyt.co](mailto:nick@nickyt.co)
    
- Location
    
    Montréal, Québec, Canada
    
- Education
    
    University of New Brunswick
    
- Joined
    
    Mar 11, 2017
    

• [Nov 1](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2ae3j)

- [Copy link](https://dev.to/opensauced/github-actions-a-maintainers-best-friend-488n#comment-2ae3j)

- Hide

[![Jake Peralta from Brooklyn Nine Nine saying Hella Fresh!](https://i.giphy.com/media/7A7iNCHhPpqwaNRgV1/giphy.gif)](https://i.giphy.com/media/7A7iNCHhPpqwaNRgV1/giphy.gif)

2 likes Like [ Reply](#/opensauced/github-actions-a-maintainers-best-friend-488n/comments/new/2ae3j)

[Code of Conduct](/code-of-conduct) • [Report abuse](/report-abuse)

Are you sure you want to hide this comment? It will become hidden in your post, but will still be visible via the comment's [permalink](#).

Hide child comments as well

Confirm

For further actions, you may consider blocking this person and/or [reporting abuse](/report-abuse)