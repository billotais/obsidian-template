<%*
const clientNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Knowledge/Companies")).map(path => path.split("/")[2].split(".")[0]))];
const clientName = (await tp.system.suggester((item) => item, clientNames, true, "Select Client Name"));
const fileTitle = await tp.system.prompt("Project Name", "");
const fileName = clientName + " - " + fileTitle
%>---
Client: '[[<% clientName %>]]'
Active: true
Manager:
Team:
Client Team:
Client Partner:
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



<% await tp.file.move("/Projects/" + fileName + "/" + fileName) %>
