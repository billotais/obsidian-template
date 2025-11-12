---
Date: "[[<% moment(tp.file.title,'YYYY-MM-DD').format('YYYY-MM-DD') %>]]"
tags:
  - Type/Note/Daily
cssclasses:
  - wide-page
---

> [!tip] < [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD').subtract(1, 'd').format('YYYY-MM-DD') %>|Previous]] | [[<% moment(tp.file.title,'YYYY-MM-DD').format('YYYY-MM-DD') %>]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD').add(1, 'd').format('YYYY-MM-DD') %>|Next]] >
## Activities


## Summary

> [!example] Meetings of the day
> ![[Meetings.base#Daily View]]


> [!note] Notes - Modified Today
> ![[Notes.base#Modified Today]]

## Tasks


> [!multi-column]
>
>> [!danger] Overdue
>> ```dataview
>> TASK
>> WHERE (due) AND !completed AND (due < date(this.file.name))
>> AND !contains(file.path, "Archives")
>> GROUP BY header
>> ```
> 
>> [!caution] Due Today
>> ```dataview
>> TASK
>> WHERE (due) AND !completed AND (due = date(this.file.name) )
>> AND !contains(file.path, "Archives")
>> GROUP BY header
>> ```
>

> [!multi-column]
>
>> [!todo] Upcoming
>> ```dataview
>> TASK
>> WHERE (due) AND !completed AND due > date(this.file.name) AND (due <= date(this.file.name) + dur(7 day))
>> AND !contains(file.path, "Archives")
>> GROUP BY join(list(due, header), " - ")
>> SORT due ASC
>> ```
>
>> [!success] Done Today
>> ```dataview
>> TASK
>> WHERE completion != null AND completion = date(this.file.name)
>> AND !contains(file.path, "Archives")
>> GROUP BY header
>> ```

> [!tip]- No Due Date
> ```dataview
> TASK 
> WHERE !contains(file.tags, "#Type/Note/Daily")
> AND !due AND !completed
> AND !contains(file.path, "Archives")
> GROUP BY header
> ```
> 

