
---
date:2021/03/28
---

https://lukes-leisure-note.blogspot.com/2020/10/obsidian.html

# Markdown cheet sheet
---
## Basics
**粗體**	`**粗體**`
*斜體*	`*斜體*`
_斜體_	`_斜體_`
***粗斜體***	`***粗斜體***`
~~刪除線~~	`~~刪除線~~`
`<u>底線<u>`
==螢光筆==	`==螢光筆==`
---
## Color(html style)
<font color=#FF0000>紅色</font>
<font color=#FF6600>橘色</font>
<font color=#FFD700>深黃色</font>
<font color=#FFFF00>黃色</font>
<font color=#00FF00>綠色</font>
<font color=#008000>深綠色</font>
<font color=#00FFFF>藍色</font>
<font color=#0000FF>深藍色</font>
<font color=#FF00FF>粉紅色</font>
<font color=#808080>灰色</font>
---
## Programming
```python
import pandas as pd
for i in range():
```
---
## Link
### Content link
#### 1. Link to a pane
`[[pane]]`
    
#### 2. Link to Headings of a pane 
`[[pane#H2]]`

#### 3. Link to block of a pane 
`[[pane^list or a paragraph]]`

#### 4. Show detail of another pane
`![[pagename]]`:show detail of another pane

### Hyperlink
[Google首頁](https://www.google.com/)  
`[Google首頁](https://www.google.com/) `
	
---

## 註腳???
文章內容 ^1
文章內容 [^other]

---

## 引用
>222
>>33333
>>>44444

---

## Front matter
YAML
`---markdown
date:2021/03/28  
tags:["obsidian","markdown"]  
aliases:  
別名  

---`

---
---
# Obsidian Hotkeys
`⌘,`:settings
`⌘o`:search for file
`⌘p`:search for hotkeys

`⌘1`:toggle left sidebar
`⌘2`:toggle right sidebar
`⌘e`:edit/view mode
`⇧⌥→`:go to any pane
`⇧⌃→`:split pane horizontally
`⇧⌃↓`:split pane vertically


---
---
# Vim hotkeys
## navigation
`shift+v`:choose multiple lines at a time
`d`:delete
