# Command Modules
Command modules provide the ability to run any command on your endpoints.  The command can be an existing command available from Windows command line or may be something such as an exe that can be included with the module.  If installing an exe, it must support
silent installation and you must provide the correct silent flags.
Modules are then assigned to policies to control how they deployed to the target computers.  They can also be deployed to a single computer without the need of creating a policy by using the Instant Module runner.

<br />
<br />

## Search
The search page allows you to view, delete, and archive existing modules. When a module is no longer needed, best practice is to archive the module. 
Archiving a module keeps all historical data about the module and if the module is needed again at a later date, it can easily be restored.
<br />
Command modules can be filtered by the module name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected modules
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## New
The new page allows you to create a new software module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the module does.
Command | The command to execute. Typicall no arguments should be included in this field, but some commands may require locating it here. If the command's path is included in the system environmental variables path, then only the command name is needed. Otherwise, the full path to the command is needed. 
Arguments | The arguments field is used to pass any arguments to the command. For example if you wanted to disable hibernation, the command would be **powercfg.exe** and the arguments would be **/h off**.
Working Directory | The directory the command is run from. If this is left blank it default to %SYSTEMROOT%\system32.
Timeout | A timeout value where the installation should give up, specified in minutes. The default value is 0 or unlimited.
Log Standard Output | If this is enabled, any output from the installation will try to be written to the log file on the client.
Log Standard Error | If this is enabled, any errors from the installation will try to be written to the log file on the client.
Success Codes | Success codes are very important. The only way Theopenem can recognize if an installation was successful is by the exit code that is returned to it. If this exit code matches any number in this field, it is marked as successful. The default value for a command module is 0. You should modify this field only if you know that command uses a different exit code success value. Each value must be separated by only a single comma.
Run As | By default, commands run as the local system account. If you need to modify this behavior, you can create an impersonation account under Admin->Impersonation Accounts, and assign it here.

#### Actions
Action | Description
------|------------
Add Module | Creates the module with the options specified in the fields

<br />
<br />

## Archived
The archived page allows you view, restore, and permanently delete archived modules.  
<br />
Archived software modules can be filtered by the module name.

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes all of the selected modules 

> [!NOTE]
> The following additional pages are available after a module is added or when selecting the view button on a specific module from the search page.

<br />
<br />

## General
The General page allows you to update the general options for the module.  It shows the same options as the New page, with the exception of the following additional fields.

Field | Description
------|------------
GUID | Each module is automatically assigned a guid for an id. This is read only and only for reference.

#### Actions
Action | Description
------|------------
Update Module | Updates the module with any changes you have made
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 

<br />
<br />

## Upload Files
The upload files page is where you add any additional files required by the command module. Uploading command module files will accept any file type. 
Finally, if you are using multiple Client Communication Servers, you will be prompted to replicate the files to all servers when uploading is complete. 
You must stay on the upload files page while files are uploading, navigating to a different page will stop the upload.<br />

Files can be selected from the **Select Files** button or by drag and drop into the file box.  Click **Upload** when you are ready to upload all of the selected files.  There is no Actions drop down button to upload the files.
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

<br />
<br />

## External Files
External files provide an additional way to add files to the module. Instead of uploading an existing file from your computer, you can download directly from a URL. External files were mainly created to share policies. 
Policies can be exported and imported by other users. If external files are used, once the policy is imported it will also automatically download any required files. 
<br/>
**To download external files:**

* Enter a file name
* Provide the url
* Optionally provide a sha256 checksum, if the checksum doesn't match after the file is downloaded, it will be deleted.
* Click Add
* Once all files are added, click Actions, then Download Files

<br/>
File Downloads run async, you can navigate away from the page once the download starts
Finally there is button to sync servers when downloads are complete, this should be enabled before starting the download if you want to replicate all Client Communication Servers when complete.

#### Actions
Action | Description
------|------------
Download Files | Downloads all files that have been specified in the grid
Archive Module | Archives the current module
Delete Module | Permanently deletes the current module 