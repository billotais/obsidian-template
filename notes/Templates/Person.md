<%*  
const clientNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Knowledge/Companies")).map(path => path.split("/")[2].split(".")[0]))];
const clientName = (await tp.system.suggester((item) => item, clientNames, true, "Select Company Name")); 
const firstName = await tp.system.prompt("First Name", ""); 
const lastName = await tp.system.prompt("Last Name", ""); 
const fileName = firstName + " " + lastName.toUpperCase()
%>---
First Name: <% firstName %>
Last Name: <% lastName %>
Company: '[[<% clientName %>]]'
Role: 
Hierarchy:
Team:
tags:
  - Type/Person
---

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


<% await tp.file.move("/Knowledge/People/" + fileName) %>