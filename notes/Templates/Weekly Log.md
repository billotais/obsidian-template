<%*
const projectNames = [
  ...new Set(
    app.vault
      .getMarkdownFiles()
      .map(f => f.path)
      .filter(path => path.startsWith("Projects"))
      .map(path => path.split("/")[1].split(".")[0])
  )
];

const projectName = await tp.system.suggester(
  (item) => item,
  projectNames,
  true,
  "Select Project Name"
);

// Week handling
const weekStart = moment().startOf("isoWeek");
const weekLabel = weekStart.format("YYYY-[W]WW");

const fileName = `${projectName.split(" - ")[0]} - Weekly Log - ${weekLabel}`;
%>---
Project: '[[<% projectName %>]]'
Week: '<% weekLabel %>'
Date: '<% weekStart.format("YYYY-MM-DD") %>'
Note Name: 'Weekly Log - <% weekLabel %>'
tags:
  - Type/WeeklyLog
---
<% await tp.file.move(`/Projects/${projectName}/Logs/${fileName}`) %>
## Monday (<% weekStart.format("YYYY-MM-DD") %>)
-
## Tuesday
-
## Wednesday
-
## Thursday
-
## Friday
-
## Weekly Summary
-

## Decisions / Notes
-

## Blockers
-

## Next Steps
-
