---
Type:
  - Project
tags: 
Status: 🟡 New
Short Description:
---
{{currentFolder}}
## Tasks
- [ ] Put task for {{ title }} here

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
