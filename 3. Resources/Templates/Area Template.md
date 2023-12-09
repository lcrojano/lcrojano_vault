<%*
const folders = tp.file.folder(true).split('/') 
let parentFolder = folders[folders.length - 1]
let title = tp.file.title 
title = await tp.system.prompt("Title", parentFolder); 
await tp.file.rename(title); 
tR += "---" 
%>
Type: Project
tags: [projects/<% await title.replace(/ /g, "-") %>]
Status: 🟡 New
Short Description:
Date Started: <% tp.file.creation_date() %>
---
> 🌟 **Embrace the Challenge:** 
> This project is your opportunity to transform aspirations into reality. Embark on a journey of growth and discovery, where your skills and determination converge to achieve meaningful goals.

- [ ] Project: <% title %> 🛫 <% tp.file.creation_date() %>
## 🎯 **Standards of Performance**
[💡^]: standard of performance (or a “quality bar”) for the product you are responsible for. 
[💡^]: Balance, peace, and meaning. 

## ✅ **Tasks**

- [ ] **Actionable task 1:** 
- [ ] **Actionable task 2:** 


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

<% tp.web.daily_quote() %>
