---
Type:
  - Project
Short Description: Setup templates for data types
tags:
  - projects/template-system
---

### Reviews
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])

```

## Resources
``` dataview
LIST 
FROM "3. Resources"
WHERE contains(file.tags,this.file.tags[0])
```