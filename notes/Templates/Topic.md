<%*  
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name")); 
const fileTitle = await tp.system.prompt("Task Name", ""); 
const fileName = fileTitle
%>---
Name: '[[<% fileTitle %>]]'
Project: '[[<% projectName %>]]'
Started: false
Completed: false
Description: 
tags:
  - Type/Topic
---


> [!quote] Meetings
> ![[Meetings.base#Topics View]]

> [!NOTE] Notes
> ![[Notes.base#Topics View]]


------------------------------


<% await tp.file.move("/Projects/" + projectName + "/Topics/" + fileName) %>