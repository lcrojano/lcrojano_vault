---
topic:
  - vim
  - how to
---
## Cut and paste one line:

1. Enter edit mode with `i` (or `I` to start editing at the beginning of the line, or `a` to append after the cursor).
2. Use `dd` to cut the line.
3. Move to the target line.
4. Use `p` to paste the cut line below the current line or `P` to paste it above the current line.

## Multiple Lines

1. Enter edit mode with `i` (or `I` to start editing at the beginning of the line, or `a` to append after the cursor).
2. Use `V` to enter visual line mode, allowing you to select multiple lines.
3. Press `d` to cut the selected text.
4. Move the cursor to the target line.
5. Use `p` to paste the cut lines below the current line or `P` to paste them above the current line.