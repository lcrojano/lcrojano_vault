---
tags:
  - resources/daybook
---


### NOTES
- [[What is a Daybook]]
- [[SSH tunnel]]
### Journal
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])
```

