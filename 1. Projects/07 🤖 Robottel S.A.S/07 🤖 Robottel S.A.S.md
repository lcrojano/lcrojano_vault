---
Type:
  - Project
tags:
  - projects/07-Robottel
Status: 🟡 New
Short Description: 
Date Started: 2023-12-14 11:24
---
#areas/🚀-05-🏘️-Family 

- [ ] Project: 07 🤖 Robottel S.A.S 🛫 2023-12-14 11:24 📅 2023-12-20 
## 🎯 **Goals**
[💡^]: Remember to set [[S.M.A.R.T]] 
[💡^]: Use the [[5 Whys Technique - Root Cause Analysis]]
[💡^]: goals excitement, achievement, and recognition
### 🏁 Outcomes
- Create an e-commerce
- Script to automatic update product from syscom
## ✅ **Tasks**

- [ ] Check Api at [SYSCOM Colombia Dev](https://developers.syscomcolombia.com/docs)
- [ ] Define if it's odoo still worthy


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

> [!quote] The conditions of conquest are always easy. We have but to toil awhile, endure awhile, believe always, and never turn back.
> — Seneca the Younger
