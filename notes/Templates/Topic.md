<%*
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name"));
const fileTitle = await tp.system.prompt("Task Name", "");
const fileName = projectName.split(" - ")[0] + " - " + fileTitle
%>---
Name: '[[<% fileName %>]]'
Project: '[[<% projectName %>]]'
Started: false
Completed: false
Description:
tags:
  - Type/Topic
---




------------------------------


<% await tp.file.move("/Projects/" + projectName + "/Topics/" + fileName) %>
