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
Division:
Departed: false
tags:
  - Type/Person
---


<% await tp.file.move("/Knowledge/People/" + fileName) %>
