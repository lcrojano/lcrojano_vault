---
Type:
  - Project
Short Description: Create a online course
tags:
  - projects/janeth-course
---
## Tasks
- [-] Planning meeting 📅 2023-11-14 5:00 pm 🔼
- [ ] Build presentation
- [ ] Setup 3 Scenes or more
- [ ] Check [[04 Setup]]
- [ ] Check [[02 Requirements]]

### Related Projects
``` dataview
LIST 
FROM "1. Projects"
WHERE contains(file.tags,this.file.tags[0])
```
## Resources
``` dataview
LIST 
FROM "3. Resources"
WHERE contains(file.tags,this.file.tags[0])
```

### Reviews
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```


## Notes 

``` dataview
LIST 
FROM "1. Projects/0003 Janeth Course"
SORT file.title
```



