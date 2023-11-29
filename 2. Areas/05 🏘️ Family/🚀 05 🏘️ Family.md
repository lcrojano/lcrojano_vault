---
Type: Project
tags: [🚀-05-🏘️-Family]
Status: 🟡 New
Short Description:
Date Started: 2023-11-29 16:22
---
## 🎯 **Goals**
[💡^]: Remember to set [[S.M.A.R.T]] goals
[💡^]: Use the [[5 Whys Technique - Root Cause Analysis]]
- To be accountable 
## ✅ **Tasks**

- [ ] Pay nidia movistar line 🔼 🔁 every month ⏳ 2023-12-24 📅 2024-03-25
- [x] Pay nidia movistar line 🔼 🔁 every month ⏳ 2023-11-25 📅 2024-02-25 ✅ 2023-11-29


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

> [!quote] Don't believe what your eyes are telling you. All they show is limitation. Look with your understanding, find out what you already know, and you'll see the way to fly.
> — Richard Bach
