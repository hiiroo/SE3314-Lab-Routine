This contribution guide is aiming to guide contributor candidates. This project is a documentation project to document laboratory routine of a software engineering course. Therefore, main contributors are considered as students who benefit most and may contribute most from their experiences. 
## Table of Contents

- [[#Getting Started|Getting Started]]
- [[#Quality Standards|Quality Standards]]
	- [[#Quality Standards#Screenshots|Screenshots]]
	- [[#Quality Standards#Code Snippets|Code Snippets]]
	- [[#Quality Standards#Text Standards|Text Standards]]
- [[#Obsidian Plugins|Obsidian Plugins]]
## Getting Started

1. Have a GitHub account.
2. Open an issue or show your intent in an existing issue.
3. Have git and Obsidian installed.
4. Create a fork from this repository.
5. Clone repository to your computer.
6. Commit your changes to your own fork using commit message standard.
```
Issue - <issue number for this feature>
- Added creating a project on Windows.
```
7. Push your changes to your own fork.
8. Create a pull request on the main repository for a document review.
## Quality Standards

### Screenshots

1. Screenshots should cover entire application window. 
	1. For Windows, [Snip Tool](https://support.microsoft.com/en-us/windows/use-snipping-tool-to-capture-screenshots-00246869-1843-655f-f220-97299b865f6b) with **Window** option can be used.
	2. For macOS, `CMD+Shift+5` with **Capture Selected Window** option can be used.
	3. For Linux, good first issue.
2. Screenshot should not contain any confidential information about the user.
### Code Snippets

1. Code snipets should be created in block with proper language annotation as follows.
	``` python
	print("Hello")
	```
### Text Standards

- Highest title should be Level 2 title in the document.
- There should be no space between a title and preceding line of last section.
- There should be a space between title and the first line of the text.
- Only `-` should be used for bullet points, not star `*`.
- All text input, output and values should be written in code quotes `code/variable/version`.
- Menu items of software tool names should be writen in bold, for instance; **Visual Studio Code**.
- Inline informational quote should not exceed two lines and
  >[!INFO] Lorem ipsum...
- Multiline information quote should have text started in a new line.
>[!INFO]
>Lorem ipsum dolor ...
- Inline warning quote should not exceed two lines and
  >[!WARNING] Lorem ipsum...
- Multiline warning quote should have text started in a new line.
  >[!WARNING]
  >Lorem ipsum dolor ...
## Obsidian Plugins

- Paste URL into Selection
- Table of Contents