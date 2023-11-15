
# Books
### 📖 Reading now

``` dataview 
TABLE pages, current-page, status, file.cday as "Started", file.mday as "Last Read"
WHERE contains(type, "Book")
AND (status = "Reading" OR status = "New")
FLATTEN choice(status = "New", "<b>📚" + status + "</b>", status) as status 
FLATTEN choice(status = "Reading", "<i>🚀" + status + "</i>", status) as status 
FLATTEN choice(status = "Completed", "<s>✅" + status + "</s>", status) as status
SORT status DESC SORT current-page  DESC
```
### ✅  Completed
``` dataview 
TABLE file.mday AS "Date Finished", status
WHERE contains(Type,"Book")
AND status = "Completed"
FLATTEN choice(status = "New", "<b>📚" + status + "</b>", status) as status 
FLATTEN choice(status = "ready", "<i>🚀" + status + "</i>", status) as status 
FLATTEN choice(status = "Completed", "<s>✅" + status + "</s>", status) as status
```


---
# ☑️ Task
``` dataview 
TABLE  date-started, date-finished, status
WHERE contains(type, "Task")
SORT date-started
FLATTEN choice(status = "New", "<b>📚" + status + "</b>", status) as status 
FLATTEN choice(status = "ready", "<i>🚀" + status + "</i>", status) as status 
FLATTEN choice(status = "done", "<s>✅" + status + "</s>", status) as status
```



---
# ✍🏻 Blog
``` dataview 
TABLE   date-started, date-finished,status
WHERE contains(type, "Blog")
SORT date-started
FLATTEN choice(status = "New", "<b>📚" + status + "</b>", status) as status 
FLATTEN choice(status = "ready", "<i>🚀" + status + "</i>", status) as status 
FLATTEN choice(status = "done", "<s>✅" + status + "</s>", status) as status
```



## 📕 Books task
``` dataview
TASK
WHERE contains(type,"Book")
```


# 📄 Notes
``` dataview
TABLE status
WHERE contains(type, "Note") AND  !contains(status, "Completed")
SORT status
FLATTEN choice(status = "New", "<b>📚" + status + "</b>", status) as status 
FLATTEN choice(status = "In-Progress", "<i>⌛" + status + "</i>", status) as status 
FLATTEN choice(status = "ready", "<i>🚀" + status + "</i>", status) as status 
FLATTEN choice(status = "Completed", "<s>✅" + status + "</s>", status) as status
```


