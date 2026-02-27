<%*
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name"));
const fileTitle = await tp.system.prompt("Note Name", "");


const topicsNames = [""].concat([... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects/" + projectName + "/Topics")).map(path => path.split("/")[3].split(".")[0]))]);

const topic = await tp.system.suggester(
(item) => item === "" ? "(no topic)" : item, // label shown in UI
topicsNames,
false,
"Select Topic Name"
);

const fileName = projectName.split(" - ")[0] + " - " + fileTitle
%>---
Project: '[[<% projectName %>]]'
Topics:
<%* if (topic) { %>
- '[[<% topic %>]]'
<%* } %>
Note Name: '<% fileTitle %>'
Summary:
tags:
  - Type/Note/Topic
Date: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
---
<% await tp.file.move("/Projects/" + projectName + "/Notes/" + fileName) %>
