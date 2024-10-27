---
tags: template
description: Daily Work Notes
hooks.newPage:
  suggestedName: "*workdev/journal/{{today}}"
  confirmName: true
  openIfExists: true
  forPrefix: "*workdev/journal/"
  tags: #workjournaldev
  command: "New Work Note Dev"
  key: "Alt-Shift-i"
frontmatter: 
  pn: "{{CleanPN(@page.name)}}"
  pp: "{{CleanPNPre(@page.name)}}"
  px: "{{CleanPNNxt(@page.name)}}"
---
# Early Thoughts
|^|
___
# To-Do
- [ ]  📅{{tomorrow}}

---
# Meetings

---
# Actual Work
