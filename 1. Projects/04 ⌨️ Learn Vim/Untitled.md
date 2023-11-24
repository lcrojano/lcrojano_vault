``` dataview 
list 
where file.type = "directory" 
group by file.name and file.depth 
sort 
file.depth asc
```
