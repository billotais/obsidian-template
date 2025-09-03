<%*  
const clientNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Knowledge/Companies")).map(path => path.split("/")[2].split(".")[0]))];
const clientName = (await tp.system.suggester((item) => item, clientNames, true, "Select Client Name")); 
const fileTitle = await tp.system.prompt("Project Name", ""); 
const fileName = clientName + " - " + fileTitle
%>---
Client: '[[<% clientName %>]]'
Active: true
Team: 
Manager: []
Technologies: 
Summary:
Stage:
Start Date: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
End Date:
tags:
  - Type/Project
---
# Admin

## Imputation

| Number | Description |
| ---- | ---- |
| **X** | Y |
# Description


# Topics

> [!task] Topics
> ![[Topics.base#Projects View]]

# History

> [!quote] Meetings
> ![[Meetings.base#Projects View]]

> [!NOTE] Notes
![[Notes.base#Projects View]]


> [!example] Open Tasks
> ```dataview
> TASK
> WHERE Project = this.file.link
> AND (status = " " OR status = "/")
> SORT file.Date DESC
> GROUP BY file.link 
> ```

> [!summary] Daily Activities and News
> ```dataview
> Table  rows.L.text as Notes
> from "Agenda"
> flatten file.lists as L
> where (contains(this.file.inlinks, file.link) and
> contains(L.text, this.file.name)) or contains(meta(L.section).subpath, this.file.name)
> group by file.link as Date
> sort Date desc
> ```
> 




<% await tp.file.move("/Projects/" + fileName + "/" + fileName) %>