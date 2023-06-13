# WinPE Modules
WinPE modules are used as an alternative way to boot your machines when deploying images.  Instead of needing to boot through PXE or USB.  You deploy directly from the Toec Client.  This assumes the computer is booted into Windows and has Toec installed.
The module is then assigned to a computer / group where you can then deploy the image.  More information can be found at [Select A Boot Method](https://docs.theopenem.com/imaging/boot-method.html#toec-winpe-module)

<br />
<br />

## Search
The search page allows you to view, delete, and archive existing modules. When a module is no longer needed, best practice is to archive the module. 
Archiving a module keeps all historical data about the module and if the module is needed again at a later date, it can easily be restored.
<br />
WinPE modules can be filtered by the module name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected modules
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## New
The new page allows you to create a new WinPE module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the module does.


#### Actions
Action | Description
------|------------
Add Module | Creates the module with the options specified in the fields

<br />
<br />

## Archived
The archived page allows you view, restore, and permanently delete archived modules.  
<br />
Archived WinPE modules can be filtered by the module name.

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes all of the selected modules 

> [!NOTE]
> The following additional pages are available after a module is added or when selecting the view button on a specific module from the search page.

<br />
<br />

## General
The General page allows you to update the general options for the module.  It shows the same options as the New page

#### Actions
Action | Description
------|------------
Update Module | Updates the module with any changes you have made
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 

<br />
<br />

## Upload Files
The upload files page is where you add or remove your WinPE files.  There must only be 2 files that are uploaded and they should not be renamed, boot.sdi and WinPE10x64.wim
If you are using multiple Client Communication Servers, you will be prompted to replicate the files to all servers when uploading is complete. 
You must stay on the upload files page while files are uploading, navigating to a different page will stop the upload.<br />

Files can be select from the **Select Files** button or by drag and drop into the file box.  Click **Upload** when you are ready to upload all of the selected files.  There is no Actions drop down button to upload the files.
#### Actions
Action | Description
------|------------
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 

<br />
<br />

## Usages
The usages page allows you quickly see which Polices, Computers, or Groups currently have the module assigned to them.  Use the **Usage Type** drop down list to switch b/w Policies, Groups, or Computers.
#### Actions
Action | Description
------|------------
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 

<br />
<br />

## Categories
Categories operate like tags and allow you to organize your modules and filter by them on the search page. Categories can be defined in Global Properties->Categories
#### Actions
Action | Description
------|------------
Update Module | Updates the module with any of the selected categories
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 


