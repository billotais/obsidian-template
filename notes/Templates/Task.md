<%*
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name")); const fileName = await tp.system.prompt("Task Name", "");
%>---
Project: '[[<% projectName %>]]'
Task: '<% fileName %>'
Task State: 'ⴵ'
tags:
  - Type/Note/Task
Created On: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
Due On:
Priority:

---
<% await tp.file.move("/Projects/" + projectName + "/Tasks/" + projectName.split(" - ")[0] + " - " + fileName + " - " + tp.date.now("YYYY-MM-DD")) %>
