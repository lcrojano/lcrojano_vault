---
Type:
  - Project
tags:
  - projects/marieannegrace-com
Status: 🟡 New
Short Description: Build top-notch website for a renowned speaker
---
## Tasks
- [ ] Put task for here

---
### Reviews
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```


### Related Projects

``` dataview
LIST 
FROM "1. Projects"
WHERE contains(file.tags,this.file.tags[0])
```

### Resources
``` dataview
LIST 
FROM "3. Resources"
WHERE contains(file.tags,this.file.tags[0])
```
