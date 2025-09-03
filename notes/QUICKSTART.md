---
Type: README
tags:
  - Type/Note
Author: https://github.com/billotais
---

# Obsidian Presentation

**Overview of Obsidian features**

You can follow this guide to understand how to use obsidian.

# Why obsidian

With traditional note taking tools like Onenote, it's often hard to find the information you are looking for if you don't stay consistant in naming, organizing your notes. And it is time consuming to do it. 

The locked-down nature of such applications also make note sharing cumbersome.

Obsidian solves theses issue with powerful note organisation features, the usage of markdown for notes, and almost unlimited customizability (including nice themes).

This quickstart illustrates some of these features.


# Note taking

## Metadata

See above. You can add any metadata to any notes you wish. These can be used by plugins like `dataview` to find your notes easily

## Markdown 

Can take [[Markdown]] notes, use the usual *styling* such as **bold**, *italic*, ~~strikethrough~~.
Can do various lists:
- Bullet point
	1. Numbered
	2. List

And also tasks
- [ ] Todo [due:: 2025-03-03] [priority:: high] 
- [/] In progress   [scheduled:: 2025-03-03]  [due:: 2025-03-04]
- [x] Done  [completion:: 2025-03-02]

Can add tables

| Column 1     | Column 2     |
| ------------ | ------------ |
| Some content | in the table |

Can add `monospace`content, and code blocks

```python
def f(x):
	if x > 10:
		print(x)
```

And latex formula
$\sum_{x=0}^{n} x^2$ 

> [!IMPORTANT]
> You can also create callouts for important comments
> 

Or add quotes
> This is a quote

## Diagrams/Images

You can easily embed content in the notes

For example images
![[Pasted image 20250302153646.png]]


PDF files 
![[sample.pdf]]

Or escalidraw diagrams and embeded them directly

![[QUICKSTART 2025-03-02 15.37.46.excalidraw]]


They will all be added to the `_attachments/` folder in your current location.

## Links and references
You can make references to other pages with [[Company X - Note]], use tags #Data/AI

You can also make links with preview, e.g. here with the [[Company X]] page:
![[Company X]]

Or event to specific section, e.g. [Python#Documentation]]
![[Python#Documentation]]

Then you can use the `dataview` plugin to make queries, e.g. to show all tasks

```sql
TASK
GROUP BY header
```
```dataview
TASK
GROUP BY header
```

# Obsidian Usage

## UI

The various sections of the UI can be customized and moved around freely. In the template, it is organized as follows

**Left side**
- File explorer (can also show search)
- Bookmarks section
- Tags

**Right side**
- Calendar (can also show incoming/outgoing links, file properties and table options)
- Note outline (can also see local graph)
- Recent files

## File storage

All notes are stored as markdown on your file system
![[Pasted image 20250302153722.png]]
This template comes with auto folder organisation when using the templates to create new pages, but you can use whatever folder structure you prefer.

These file can be easily shared, backed-up, etc. For instance, if you need to share all notes for a give project, just copy the project folder and send it.

Having the files on your computer means you can easily put them in a Google Drive/OneDrive, or use `git` to backup your files. Or use the official 5$/month Obsidian Sync (E2E encrypted).

You can also just export any page to a pdf.


## PAKMAT Approach

The `PAKMAT` structure defines how notes are organized.

**`Projects`:** One folder per project, with the company and project name as the folder name. Each project folder contains:
- `Company - Project.md`  : the main file for the project, containg the overview
- `Meetings`: One file per meeting, with the meeting name and date as the file name
- `Notes`: One file per note, with the company and note name as the file name
- `Topics`: One file per topic, with the topic name as the file name

**`Archive`:** When a project is finished, I move its folder from the `Projects` folder to the `Archive` folder.

**`Knowledge`:** Contains all the general knowledge notes, with subfolders for:
  - `Companies`: One file per company
  - `Concepts`: One file per concept
  - `People`: One file per person
  
**`Media`:** Used to store images, that I reuse across mutliple projects (e.g. icons)

**`Agenda`:** Contains one file per day, with the date as the file name. This is where I keep my daily notes, giving me an overview of what I did each day and active tasks.

**`Templates`:** Contains the templates files 

## How to use

**Finding notes**

I usually use the ctrl-O (cmd-O on MacOS) to quickly open a file. There, by typing the project/company name and some keywork from the note name I can usually find what I'm looking for. If not, I go through a project page or person page to see all related notes. As a last resort, I can also use the search.

**Creating notes**

My main interaction is through the **ctrl-N** (cmd-N on MacOs) shortcut to create a new note. I then select the template I want to use, and it asks me for various mandatory information depending on the type of note. This information is required as creation time as it is used to give the correct name to the new file, as save it to the correct folder.

- `Company`: Asks for the Company Name
- `Person`: Asks for the Company, First Name and Last Name
- `Project`: Asks the the Company and Project Name
- `Note`: Asks for the Project and Note name
- `Meeting`: Asks for the Project and Meeting name
- `Concept`: Asks for the Concept name
- `Topic`: Asks for the Project and Topic name

The files will automatically be created in the correct folder, with the correct name. Folders are created automatically if they don't exist yet.
When adding attachements like images or *escalidraw* diagrams, they will be automatically added to a `_attachments` folder in the same folder as the note.

It is also possible to apply a template to a note with **alt-e**, for instance if a concept was first refered to by using the obsidian link synatx `[[Concept]]`, and that you the want to create the note for that concept.


### Workflow example

**New project
- Create `Company`
- Create `Project`, add description

**Complex topic for a specific project**
- Create `Note`, linking it to the project

**Quick note for a project**
- Go to daily view, add header with project and bullet point/task

**Need to prepare a meeting**
- Create `Meeting`, fill the *topics* section and add participants

**Search for latest meetig with [[John DOE]]:**
- Go to the person's page and see all meetings

**See quick notes for a project**
- Go to project page, under the *History* section in Daily activities
## Plugins

The template comes with a few plugins that I find essential for my workflow. Not all are required, but they all add some functionality that I find useful. 

- **Advanced Tables**: For easier usage of markdown tables
- **Calendar**: For easy access to the daily notes
- **Custom File Explorer Sorting**: To keep the folders in the correct order
- **Dataview**: For some queries in the various overview pages. Most queries are using Bases.
- **Escalidraw**: My prefered drawing tool for obsidian. I use the ctrl+alt+D to create an embedded a new drawing in the current note.
- **Folder Note**: To automatically create open the main folder note when opening a folder
- **Iconize**: To add icons to the folders
- **Minimal Theme Settings**: additonal settings for the minimal theme that I use
- **Recent File**: Quick access to recently opened files
- **Style Settings**: Additional settings to control the style, allowing for instance the double column layout in the daily notes.
- **Tag Wrangler**: For easier tag management, including bulk renaming
- **Tasks**: Allow the creation of tasks with due dates, and easier checking of tasks in progress or done
- **Templater**: For the creation of new notes with templates

You can also check the official Web Clipper extension (https://obsidian.md/clipper), allowing you to easily export web pages to obsidian with one click, and to define custom templates to parse the webpage.