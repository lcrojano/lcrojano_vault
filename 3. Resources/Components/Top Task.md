### Top Priority

``` dataview
TASK
WHERE (contains(text,"🔺")) AND !completed
AND due <= date(today)
FLATTEN file.list as l
SORT date ASCENDING
```
### Other Tasks 
``` dataview
TASK
WHERE (contains(text,"⏫")) AND !completed
AND due <= date(today)
FLATTEN file.list as l

SORT date ASCENDING
```