# Printer Modules
Printer modules provide the ability to install and remove network printers.  It should be noted that it currently only supports network printers.  The module does not handle installing print drivers.  Printer modules are then 
assigned to policies to control how they deployed to the target computers.  They can also be deployed to a single computer without the need of creating a policy by using the Instant Module runner.

<br />
<br />

## Search
The search page allows you to view, delete, and archive existing modules. When a module is no longer needed, best practice is to archive the module. 
Archiving a module keeps all historical data about the module and if the module is needed again at a later date, it can easily be restored.
<br />
Printer modules can be filtered by the module name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected modules
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## New
The new page allows you to create a new Printer module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the module does.
Network Path | The UNC path of the printer, such as **\\myprintserver\printer1**
Action | The action that should be taken with the printer. Install and Delete are self explanatory. None means nothing with the printer will happen and is really only used as a way to restart the printer spooler. InstallPowershell is just an alternative way to install the printer in case the default install option has problems.
Set As Default | Sets the printer as default. A policy may contain multiple printer modules. The last printer module to run with set as default, will become the default printer.
Restart Print Spooler | If this is enabled the printer spooler service will be restarted after the printer is installed.
Wait For Enumeration | If this is enabled, the policy won't continue until it verifies the printer was installed.  Be careful with this setting, you can easily prevent additional policies from running while waiting.

#### Actions
Action | Description
------|------------
Add Module | Creates the module with the options specified in the fields

<br />
<br />

## Archived
The archived page allows you view, restore, and permanently delete archived modules.  
<br />
Archived Printer modules can be filtered by the module name.

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


