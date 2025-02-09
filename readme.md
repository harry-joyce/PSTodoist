﻿# PSTodoist
## About PSTodoist
 A powershell module that uses the Todoist REST V2 api.

 This module or author is NOT affiliated with TODOIST.

## Download

### Latest build
https://github.com/harry-joyce/PSTodoist/archive/refs/tags/1.0.zip

## Install
See [install](install.md)

## Help
 Refer to [the docs](docs/en-us/PSTodoist.md)

## Get API-token from todoist.
On the todoist website, go to: Todoist Settings -> Account -> API token.

## Usage
You can either set the todoist token with:

```Powershell
Set-TodoistToken -Token <YourToken>
```

Or supply it as a parameter on every command

```Powershell
Get-TodoistTask -Token <Yourtoken>
```

### Some examples:

```Powershell
Set-TodoistToken -Token abcdef12345
Get-TodoistTask | Where-Object {$_.Content -eq "Do dishes"} | Update-TodoistTask -Content "Buy dishwasher"

Set-TodoistToken -Token abcdef12345
$Task = Get-TodoistTask | Where-Object {$_.Content -eq "Do dishes"}

# To close task
$Task | Close-TodoistTask

# To reopen Task
$Task | Open-Todoist Task

# To update task with class method
$Task.Content = 'Buy dishwasher'
$Task.Update()

# To close task with class method
$Task.Close()

# To update a class with function
Update-TodoistTask -Id $Task.Id -Content "Buy cheap dishwasher"

# To add comment to task
$Task | New-TodoistComment -Category Task -Content "Researched dishwashers online"

# To add comment with a file to task
$Task | New-TodoistComment -Category Task -Content "PDF of dishwasher" -AddAttachment -AttachmentResourceType "file" -AttachmentFileType "application/pdf" -AttachmentFileUrl "http://contoso.com/files/dishwasher.pdf" -AttachmentFileName "Dishwasher.pdf"

# To remove task
$Task | Remove-TodoistTask

# To create a new label
New-TodoistLabel -Name "At home"

# To create a new project
New-TodoistProject -Name "Repair dishwasher"
```




