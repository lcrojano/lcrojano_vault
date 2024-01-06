---
Type: Project
tags: [projects/04-⌨️-Learn-Vim]
Status: 🟡 New
Short Description:
Date Started: 2024-01-05 23:11
---
> 🌟 **Embrace the Challenge:** 
> This project is your opportunity to transform aspirations into reality. Embark on a journey of growth and discovery, where your skills and determination converge to achieve meaningful goals.

- [ ] Project: 04 ⌨️ Learn Vim 🛫 2024-01-05 23:11
## 🎯 **Goals**
[💡^]: Remember to set [[S.M.A.R.T]] 
[💡^]: Use the [[5 Whys Technique - Root Cause Analysis]]
[💡^]: goals excitement, achievement, and recognition
### 🏁 Outcomes
- Achieve at leas 40 rmp speed at writing on keyboard
- use vim to improve speed at coding

## ✅ **Tasks**

- [ ] Practice for 30 minutes [Learn Touch Typing Free - TypingClub](https://www.typingclub.com/)


---
## 📖 Journal Insights
[💭^]: Reflect on your progress, challenges, and inspirations throughout the project. Use this space to capture your thoughts, ideas, and emotions.

``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```

## 🗒 Notes
[💭^]: Gather relevant information, resources, and insights from other notes related to this project.
``` dataview
LIST 
WHERE file.name != this.file.name 
and  contains(file.folder, this.file.folder)
```


## 🤝 Related Projects
[💭^]: Explore connections and synergies between this project and other ongoing ventures. Identify opportunities for collaboration and knowledge sharing.
``` dataview
LIST 
FROM "1. Projects"
AND "2. Areas"
WHERE contains(file.tags,this.file.tags[0]) and file.name != this.file.name
```

## 📚 Resources
[💭^]: Compile a list of helpful tools, articles, tutorials, and external resources that can support your project's success.
``` dataview
LIST 
FROM "3. Resources"
WHERE contains(file.tags,this.file.tags[0])
```


---
**Remember:**

- **Believe in yourself:** Your potential is limitless. Embrace your abilities and trust in your capacity to achieve great things.

- **Enjoy the journey:** Learning and growth are inherent parts of any project. Embrace the challenges, celebrate the victories, and savor the entire experience.

**Embrace the excitement and embark on your journey of accomplishment!**

> [!quote] Mistakes are always forgivable, if one has the courage to admit them.
> — Bruce Lee
