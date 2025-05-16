# Script Modules
Script modules provide the ability to run custom scripts on your endpoints.  Modules are then assigned to policies to control how they deployed to the target computers.  They can also be deployed to a single computer without
the need of creating a policy by using the Instant Module runner.

<br />
<br />

## Search
The search page allows you to view, delete, and archive existing modules. When a module is no longer needed, best practice is to archive the module. 
Archiving a module keeps all historical data about the module and if the module is needed again at a later date, it can easily be restored.
<br />
Script modules can be filtered by the module name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected modules
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## New
The new page allows you to create a new Script module.

Field | Description
------|------------
Display Name | The name of the module, module names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the module does.
Script Type | There are 5 script type options, Powershell, VbScript, Batch, ImagingClientBash, and ImagingClientPowershell. The first 3 are used with Toec and can be assigned to Policies. The last 2 are specific to Client Imaging. If you want to run a custom script while using the Linux Imaging Environment, select ImagingClientBash. If you want to run a custom script while using the WinPE Imaging Environment, select ImagingClientPowershell. The script contents must be for the appropriate script type.
Arguments | The arguments field is used to pass any arguments to the script.
Working Directory | The directory the script is run from. If this is left blank it defaults to %SYSTEMROOT%\system32.
Timeout | A timeout value where the installation should give up, specified in minutes. The default value is 0 or unlimited.
Log Standard Output | If this is enabled, any output from the installation will try to be written to the log file on the client.
Log Standard Error | If this is enabled, any errors from the installation will try to be written to the log file on the client.
Add To Inventory Collection | When this is enabled, the result of the script will be added as a custom inventory attribute.  It will then be collected every time an inventory scan is ran. It is viewable under the computer's custom inventory page. This data is also usable in the custom reporting page or dynamic groups. When using this option, whatever is written on screen as the last line is what is collected. The following example collects a registry value that specifies if the computer requires Ctrl+Alt+Delete before login.  **Write-Host (Get-ItemProperty -Path "HKLM:SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" -Name DisableCAD).DisableCAD** This example script is only a single line, but your script can be as long as needed to obtain the required information, then just do a Write-Host with the value you need as the last line.
Success Codes | Success codes are very important. The only way Theopenem can recognize if an installation was successful is by the exit code that is returned to it. If this exit code matches any number in this field, it is marked as successful. The default value for a script module is 0. You should modify this field only if you know that command uses a different exit code success value. Each value must be separated by only a single comma.
Run As | By default, scripts run as the local system account. If you need to modify this behavior, you can create an impersonation account under Admin->Impersonation Accounts, and assign it here.
Script Contents | Enter the script text in this box. Scripts are not uploaded as files.
Use As Condition | When this option is enabled, the script result can be used as a condition for a policy to continue or exit. Policy module's can be set to run in a specific order, the script module condition can be ordered to test the condition at any order, but is typically set to run first. To use this option, you must set the success code to be a non standard exit code, that will match the condition met exit code in your script. The value of -1 is typically recommended. Leaving the default value of 0 could result in false positives. The following example checks if the system is 64-bit, if so it exits with code -1, signifying success and the policy should continue. If the system is not 64-bit, the policy would exit skipping any remaining assigned modules. Since the script is using -1 as success, the success code for this module must be set to -1.<br/> 
```
$arch = (Get-WmiObject Win32_OperatingSystem).OSArchitecture
if($arch -eq "64-bit") 
{ 
  Exit -1 
} 
```

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

