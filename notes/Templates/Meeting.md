<%*  
const projectNames = [... new Set(app.vault.getMarkdownFiles().map(f => f.path).filter(path => path.startsWith("Projects")).map(path => path.split("/")[1].split(".")[0]))];
const projectName = (await tp.system.suggester((item) => item, projectNames, true, "Select Project Name")); const fileTitle = await tp.system.prompt("Meeting Name", ""); 
const dayOfWeek = moment().day(); 
const dateFormat = "YYYY-MM-DD"; 
const suggestions = new Map(); 

suggestions.set("today", moment()); 
suggestions.set("tomorrow", moment().add(1, 'days')); 
suggestions.set("next monday", moment().add(1, 'weeks').day(1)); 
suggestions.set(dayOfWeek >= 2 ? "next tuesday" : "tuesday", dayOfWeek >= 2 ? moment().add(1, 'weeks').day(2) : moment().day(2) ); 
suggestions.set(dayOfWeek >= 3 ? "next wednesday" : "wednesday", dayOfWeek >= 3 ? moment().add(1, 'weeks').day(3) : moment().day(3) ); 
suggestions.set(dayOfWeek >= 4 ? "next thursday" : "thursday", dayOfWeek >= 4 ? moment().add(1, 'weeks').day(4) : moment().day(4) ); 
suggestions.set(dayOfWeek >= 5 ? "next friday" : "friday", dayOfWeek >= 5 ? moment().add(1, 'weeks').day(5) : moment().day(5) ); 
suggestions.set(dayOfWeek >= 6 ? "next saturday" : "saturday", dayOfWeek >= 6 ? moment().add(1, 'weeks').day(6) : moment().day(6) ); 
suggestions.set(dayOfWeek == 0 ? "next sunday" : "sunday", dayOfWeek >= 0 ? moment().add(1, 'weeks').day(0) : moment().day(0) ); 
suggestions.set("manual", null); 
const selection = await tp.system.suggester( [...suggestions].map(([k, v]) => k !== "manual" ? k + " (" + v.format(dateFormat) + ")" : k), Array.from(suggestions.values()) ); 
let resultDate = null; 
if (!selection) { 
    inputDate = await tp.system.prompt("Type a date (YYYY-MM-DD):"); 
    resultDate = moment(inputDate, "YYYY-MM-DD"); 
    if (!resultDate.isValid()) { 
        resultDate = moment(); 
    } 
} 
else { 
    resultDate = selection; 
}
resultDate = resultDate.format(dateFormat)
const fileName = projectName.split(" - ")[0] + " - " + fileTitle + " - " + resultDate
%>---
Project: '[[<% projectName %>]]'
Date: '[[<% resultDate %>]]'
Meeting Name: '<% fileTitle %>'
Participants:
Topics:
tags:
  - Type/Meeting/<% fileTitle.contains("Weekly") ? "Weekly" : fileTitle.contains("Monthly") ? "Monthly" : "Group" %>
Related:
---
<% await tp.file.move("/Projects/" + projectName + "/Meetings/" + fileName) %>
## Topics



## Summary



## Next tasks


