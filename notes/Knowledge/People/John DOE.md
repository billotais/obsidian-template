---
First Name: John
Last Name: DOE
Company: "[[Company X]]"
Role: CEO
Hierarchy:
tags:
  - Type/Person
Division: Data & AI
---

> [!INFO] Readme
> A #Type/Person  can be created as a sort of "contact card" All projects, meetings, notes and daily notes refering to this person will show up here.

> [!success] Projects
> ![[Projects.base#People View]]

> [!quote] Meetings
> ![[Meetings.base#People View]]

> [!example] Notes
> ![[Notes.base#People View]]

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


*[[John DOE]] is a fictive person, working at [[Company X]]*