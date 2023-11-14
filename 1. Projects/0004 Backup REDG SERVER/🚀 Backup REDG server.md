---
Type:
  - Project
tags:
  - projects/redg-server-backup
Status: 🟡 New
---

## Tasks
- [ ] Must backup projects until 📅 2023-11-19 ⏫ ⏳ 2023-11-15 

---
## Reviews
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```


## Related Projects

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

---