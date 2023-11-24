---
title: Form Data
tags: #form, #templater
---



Within the `---` block, you can add any additional frontmatter properties relevant to the note.

**2. Create Form Fields:**

Use Markdown's list syntax to create form fields. Each list item represents a single field, and the syntax allows for defining labels and input types.

markdown
### Form Fields

- **Label:** <input type="text" id="inputField1" placeholder="Enter text">
- **Label:** <input type="number" id="inputField2" placeholder="Enter number">
- **Label:** <input type="checkbox" id="checkboxField" checked> Checkbox


The `id` attribute of each input element serves as a unique identifier for the field, which will be used later to retrieve the user's input.

**3. Templater Integration:**

To integrate Templater and capture user input, utilize the `tp.getFrontmatterValue()` and `tp.getFieldValue()` methods. These methods allow you to access the frontmatter values and input field values, respectively.

markdown
### Data Capture

Frontmatter value: {{tp.getFrontmatterValue('title')}}

Input field value: {{tp.getFieldValue('inputField1')}}

