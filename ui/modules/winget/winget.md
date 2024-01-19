# Winget Modules
Winget modules provide the ability to easily install official Microsoft Winget packages on your endpoints.  Modules are then assigned to policies to control how they are deployed to the target computers.  They can also be deployed to a single computer without
the need of creating a policy by using the Instant Module runner.

<br />
<br />

## Search
The search page allows you to view, delete, and archive existing modules. When a module is no longer needed, best practice is to archive the module. 
Archiving a module keeps all historical data about the module and if the module is needed again at a later date, it can easily be restored.
<br />
Winget modules can be filtered by the module name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected modules
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## New
The new page allows you to create a new Winget module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the module does.

<br />
<br />

## Archived
The archived page allows you view, restore, and permanently delete archived modules.  
<br />
Archived Winget modules can be filtered by the module name.

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes all of the selected modules 

> [!NOTE]
> The following additional pages are available after a module is added or when selecting the view button on a specific module from the search page.

<br />
<br />

## General
The General page allows you to update the general options for the module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
GUID | Each module is automatically assigned a guid for an id. This is read only and only for reference.
Description | The description field is optional for you to give a short description for what the module does.
Assigned Package Identifier | Displays the Winget package that is currently assigned to the module, assignable from **Available Winget Packages Page**
Assigned Package Version | Displays the version of the Winget Package that is currently assigned.
Arguments | Any additional arguments you would like to send to the winget command
Override | Used to override the default parameters for a winget manifest
Auto Update | When this is enabled, the package will automatically be updated when a newer version is released.  A winget update policy is required for this to work.
Install Latest Version | When this is enabled, the latest version will be installed when installing the software for the first time on that endpoint.  For example, when selecting a Winget package, a version is also selected.  That specific version will always be installed even if a newer package is released.  If this option is enabled, a new endpoint would get the latest version of the package instead of the one that is selected.  This option has nothing to do with the previous auto update option.
Install Type | Indicates to install or uninstall the package.  I've seen many packages that don't uninstall when set to uninstall, this is the fault of that package, not Winget or Theopenem.
Timeout | A timeout value where the installation should give up, specified in minutes. The default value is 0 or unlimited.
Log Standard Output | If this is enabled, any output from the installation will try to be written to the log file on the client.
Log Standard Error | If this is enabled, any errors from the installation will try to be written to the log file on the client.
Run As | By default, Winget modules run as the local system account. If you need to modify this behavior, you can create an impersonation account under Admin->Impersonation Accounts, and assign it here.

#### Actions
Action | Description
------|------------
Update Module | Updates the module with any changes you have made
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 

<br />
<br />


## Available Winget Packages
This page allows you to select a Winget package to assign to the module.  Only 1 package can be selected per module.  The page will randomly display various packages unless you search for a specific package.
They are various filtering options available for the search that should be self explanatory.

#### Actions
Action | Description
------|------------
Assign Selected Package | Assigns the selected package to the module.
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

<br />
<br />

