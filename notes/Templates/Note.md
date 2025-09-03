<%*  
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name")); const fileName = await tp.system.prompt("Note Name", projectName.split(" - ")[0] + " - "); 
%>---
Project: '[[<% projectName %>]]'
Topics:
Summary:
tags:
  - Type/Note/Topic
Date: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
---
<% await tp.file.move("/Projects/" + projectName + "/Notes/" + fileName) %>