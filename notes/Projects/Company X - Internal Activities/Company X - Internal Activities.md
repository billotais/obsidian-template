---
Client: "[[Company X]]"
Active: true
Team:
  - "[[John DOE]]"
Manager:
  - "[[John DOE]]"
Technologies:
  - "[[Python]]"
Summary: This is an internal project
tags:
  - Type/Project
Stage: Ongoing
Start Date: 2025-01-01
End Date: 2025-12-31
---
# Admin

## Imputation

| Number | Description |
| ---- | ---- |
| **X** | Y |
# Description

[[Company X - Internal Activities]] is a project at [[Company X]]

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




