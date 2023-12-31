---
Type: Project
tags: [🚀-0004-Backup-REDG-SERVER]
Status: 🟡 New
Short Description:
Date Started: 2023-11-17 00:02
---
> 🌟 **Embrace the Challenge:** 
> This project is your opportunity to transform aspirations into reality. Embark on a journey of growth and discovery, where your skills and determination converge to achieve meaningful goals.

## 🎯 **Goals**
[💡^]: Remember to set [[S.M.A.R.T]] goals
[💡^]: Use the [[5 Whys Technique - Root Cause Analysis]]
- To backup each proyect hosted at rejean server


## ✅ **Tasks**

- [x] Must backup projects until 📅 2023-11-19 ⏫ ⏳ 2023-11-15 (60 minutes). ✅ 2023-11-17
	- [x] [[ List of projects]] ✅ 2023-11-17
	- [x] Backup databases ✅ 2023-11-17
	- [x] Backup nginx ✅ 2023-11-17
	- [x] check docker services ✅ 2023-11-17
- [ ] Transfer project to new server
	- [ ] create a droplet backup
	- [ ] Create new server for selected projects


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

> [!quote] Happiness is not in the mere possession of money; it lies in the joy of achievement, in the thrill of creative effort.
> — Franklin D. Roosevelt
