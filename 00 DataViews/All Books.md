```dataview 
Table author as Author, ("![|100](" + cover + ")") as Cover, pages, 
category as genre, rating
From "00 My Books"
Where 
contains(status, "unread")
```


