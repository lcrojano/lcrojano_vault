---
Type:
  - Note
tags:
  - javascript/best-practices
---
variable declarations are assigned to memory at [[compilation]] time and not at [[execution]] time.

this looks like  declaration **are moved to the beginning of its [[Scope]]**. (but what really happens is a [[heap loop]])

**Tip**: note that only declares variable at compiling time, and not assigns value

[[Clean Code Javascript#^x8x2vau8h4s|example]]