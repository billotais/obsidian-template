---
Provider: 
tags: Type/Concept
aliases: 
Related: 
---
# Projects
```dataview
LIST FROM #Type/Project 
WHERE contains(file.outlinks, this.file.link)
```
# Notes
```dataview
TABLE Project FROM #Type/Note/Topic
WHERE contains(file.outlinks, this.file.link)
SORT Date DESC
```
# Meetings
```dataview
TABLE Project FROM #Type/Meeting
WHERE contains(file.outlinks, this.file.link)
SORT Date DESC
```
# Documentation

<% await tp.file.move("/Knowledge/Concepts/" + tp.file.title) %>

# References
