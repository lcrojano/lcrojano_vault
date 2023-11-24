---
tags:
  - resources/daybook
---


### NOTES
- [[What is a Daybook]]
- [[SSH tunnel
- [[WSL import ext4.vhdx being blocked by system process]]]]
### Journal
``` dataview
LIST item.text
FROM "0. Daybook"
FLATTEN file.lists as item
WHERE contains(item.tags, this.file.tags[0])
```

