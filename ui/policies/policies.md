# Policies
Policies control how and when modules are deployed to your endpoints.  A module by itself does not do anything until it is assigned to a policy.  Policies are then assigned to groups to target specific computers.

<br />
<br />

## Search
The search page allows you to view, delete, archive, activate, deactivate, and clone existing policies. When a policy is no longer needed, best practice is to archive the policy. 
Archiving a policy keeps all historical data about the policy and if the policy is needed again at a later date, it can easily be restored.
<br />
Policies can be filtered by the name and category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected policies
Delete Selected | Permanently deletes all of the selected policies 

<br />
<br />

## New
The new page allows you to create a new policy.

Field | Description
------|------------
Name | The name of the policy, policy names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the policy does.

#### Actions
Action | Description
------|------------
Add Policy | Creates the policy with the options specified in the fields

<br />
<br />




## Archived
The archived page allows you view, restore, and permanently delete archived policies.  
<br />
Archived policies can be filtered by the module name.

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes all of the selected modules 

<br />
<br />

## Import
The import page allows you to import Policies that have already been created and exported by someone. An imported policy will create the policy and all required modules for that policy in a deactivated state. After the import is complete you can review the policy and activate when ready.

#### Actions
Action | Description
------|------------
Import Policy | Imports the selected policy 

<br />
<br />

## Active Policy Status
Displays a list of all active policies and the deployment status of each.


> [!NOTE]
> The following additional pages are available after a policy is added or when selecting the view button on a specific policy from the search page.

<br />
<br />

## General
The General page allows you to update the general options for the policy.

Field | Description
------|------------
Name | The name of the policy, policy names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the policy does.
Execution Type | Policies will copy all of the required files for any modules to the toec appdata folder for the entire policy before installing or running the commands. Setting the execution type to Cache will stop the policy after this occurs, preventing anything from installing. If you want to cache files ahead of time to make for a faster installation later, this is how you do it. After you have finished caching all the required files on your endpoints, flip this setting back to Install, to perform the installation.
Completed Action | Specifies the action to take after a policy has completed successfully, does not apply to a failed policy.

* **DoNothing** - Don't do anything, continue on to the next policy if any.
* **Reboot** - Reboots the computer immediately after the policy is complete.
* **RebootIfNoLogins** - Reboots the compute immediately ater the policy is complete, but only if no one is logged in.

 | 
------|------------
Error Action | Specifies what should happen if the policy encounters an error.

* **AbortCurrentPolicy** - Stops the current policy but continues with any additional policies that may apply.
* **AbortRemainingPolicies** - Stops the current policy and does not load any additional policies.
* **Continue** - Continues processing the current policy and any additional policies.

 | 
------|------------
Delete Cache | If the policy completed successfully, any files that were copied to the endpoint are removed if this option is enabled. This only applies when the execution type is set to Install.
Auto Archive | An option to automatically archive the policy

* **None** - Auto archive is disabled for the policy.
* **WhenComplete** - Archives the policy when all endpoints in the target group have reported success.
* **AfterXdays** - Archives the policy after an interval of days, the sub option Days, is available when this option is selected.

 | 
------|------------
Days | When Auto Archive is set to AfterXdays, this is number of days that must pass since the Policy Start Date, before it is archived.

 | 
------|------------
Log Level | Defines the endpoint log level for the policy. The endpoint logs are written to c:\program files\toec\logs on each endpoint.

* **Full** - Everything for the policy is written to the log file, same as DEBUG.
* **HiddenArguments** - Hides sensitive information from the log file, same as INFO.
* **None** - Does not log anything about the policy, same as OFF.

 | 
------|------------
Skip Server Logging Result | Each time an endpoint runs a policy, the result is recorded and stored in the database, viewable under the policie's client history. Some policies don't make sense to capture this information. For example, if a policy was setup to collect the inventory of an endpoint once per day, and Theopenem contained 5000 endpoints, the Client History log would get 5000 entries per day of information that isn't really needed. On the other hand, if deploying a software application to those same endpoints, it would only run once per computer and we could then easily determine which endpoints successfully installed the software if we don't skip the server logging result.



#### Actions
Action | Description
------|------------
Update Policy | Updates the policy with any changes you have made
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />


## Conditions
The conditions page is used to set various conditions for the policy.

Field | Description
------|------------
Condition | A condition can be set to limit the scope of computers to be more specific, based on a script module set as a condition
Condition Failed Action | If the condition above is not met, how should the results be recorded. Most of these options are for your own records, but there are some differences depending on the frequency.

* MarkNotApplicable - Sets the result to Not Applicable, if the frequency is set to OncePerComputer or OncePerUserPerComputer, the policy will not run again on that computer.
* MarkSkipped - Sets the result to Skipped, the policy will try to run again on every trigger
* MarkSuccess - Sets the result to Success, if the frequency is set to OncePerComputer or OncePerUserPerComputer, the policy will not run again on that computer.
* MarkFailed - Sets the fesult to Failed, the policy will try to run again on every trigger
* GotoModule - Not used in this context.

 | 
------|------------
Com Server Condition | Policies can be setup to only run when the endpoint is connected to specific Com Servers. The default value for this field is Any, meaning the policy will run regardless of the Com Server. The other option is Selective. If this is set to selective, a sub option will appear to select the Com Servers this should policy should be allowed to run from. The best use case for this is a Com Server in the DMZ. Theopenem can manage endpoints outside of your network if a Com Server is setup in your DMZ. There may be policies that require internal resources in order to complete. If the policy requires internal resources, then you could set the Com Server Condition to Selective, and check all Com Servers except the one in the DMZ. This will prevent the policy from running until the computer makes it back to your internal network.

#### Actions
Action | Description
------|------------
Update Policy | Updates the policy with any changes you have made
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Triggers
The triggers page displays various options to determine when the policy will run.

Field | Description
------|------------
Trigger | The trigger defines at which point of the client process the Policy should run, there are four options. StartupOrCheckin, Startup, Checkin, and Login. This also helps define what user the policy will run as. The decision to run the policy or not will be a combination of Trigger, Frequency, Window Schedule, Start Date, and client policy history.

* **StartupOrCheckin** - The policy will attempt to run any time the computer or service starts or checks in. All modules will run as the local system account unless the module's run as field is changed.
* **Startup** - The policy will only attempt to run when the computer or service starts. All modules will run as the local system account unless the module's run as field is changed.
* **Checkin** - The policy will only attempt to run when doing a recurring checkin, this excludes starting the service or computer. All modules will run as the local system account unless the module's run as field is changed.
* **Login** - The policy will only attempt to run when a user logs in. All modules will run in the context of that user, the user will need the appropriate permissions for whatever the modules are doing

 | 
------|------------
Frequency | The frequency defines how often a policy should run relative to the trigger type.

* **Ongoing** - The policy will run every time the trigger type is hit
* **OncePerComputer** - The policy will only run 1 time on the endpoint
* **OncePerComputerPerUser** - Only available if the Trigger is set to Login.  The policy will run 1 time for each user that logs into the computer.
* **OncePerDay** - The policy will run once per day. A new day is considered 12:00am, not 24 hours. It is possible a policy could run at 11:00pm and then 1 hour later at 12:00am.
* **OncePerWeek** - The policy will run once per calendar week. Two additional sub options are available for this frequency. Day of Week and Frequency Missed Action.
* **OncePerMonth** - The policy will run once per calendar month. Two aditional sub options are available for this frequency. Day of Month and Frequency Missed Action. Setting the day of month to 31, means to run on the last day of the month.
* **EveryXhours** - The policy will run on an hourly interval that you define. The additional sub option, Hour Interval is available for this Frequency.
* **EveryXdays** - The policy will run on a daily interval that you define. The additional sub option, Hour Interval is available for this Frequency.

 | 
------|------------
Day Of Week | The day of week is sub option that is available when the Frequency is set to OncePerWeek. This sets the day of the week the policy should run on.
Day Of Month | The day of month is sub option that is available when the Frequency is set to OncePerMonth. This sets the day of the month the policy should run on. Setting the day of month to 31, means to run on the last day of the month.
Hour Interval | The hour interval is sub option that is available when the Frequency is set to EveryXhours. The hour interval value replaces the X. An hour interval value of 5 would run the policy every 5 hours.
Day Interval | The day interval is sub option that is available when the Frequency is set to EveryXdays. The day interval value replaces the X. A day interval value of 3 would run the policy every 3 days.

 | 
------|------------
Frequency Missed Action | The frequency missed action is a sub option that is only available when the Frequency is set to OncePerWeek or OncePerMonth.

* **NextOpportunity** - If a policy frequency is missed by an endpoint, it will run at the next opportunity.
* **ScheduleDayOnly** - If a policy frequency is missed by an endpoint, it will only run if it's day of week or day of month sub option match the current day.

 | 
------|------------
Window Start Schedule | The window start schedule is a way to provide more granular control over the frequency of a policy. Schedules allow you to define specific days the policy should run, and specific time frames. Schedules can be created in Global Properties->Schedules. When using start and end schedules on a policy, both the start and end schedule must be provided, if only 1 is assigned, it will be ignored. Finally, when evaluating the days to run on, only the start schedule is used. The start schedule is also used to specify the starting time range.
Window End Schedule | The window end schedule is a way to provide more granular control over the frequency of a policy. Schedules allow you to define specific days the policy should run, and specific time frames. Schedules can be created in Global Properties->Schedules. When using start and end schedules on a policy, both the start and end schedule must be provided, if only 1 is assigned, it will be ignored. Finally, when evaluating the days to run on, only the start schedule is used. The end schedule is only used to provide the ending time range.
Start Date | Specifies the starting date the policy can be used. The start date can be dated in the future to plan policies that will execute at a later time. When using a date in the future, the policy must still be activated prior to that date.


#### Actions
Action | Description
------|------------
Update Policy | Updates the policy with any changes you have made
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Specialties
Policies can also run some specialized actions that are not related to modules.  Those actions can be configured here.

Field | Description
------|------------
Collect Inventory | Specifies if the policy should collect inventory information about the endpoint. There are four options.

* **Disabled** - Don't collect inventory with the policy.
* **Before** - Collect inventory before any assigned modules are run.
* **After** - Collect inventory after all assigned modules are run.
* **Both** - Collect inventory both before and after modules are run.

 | 
------|------------
Login Tracker | If this option is enabled, the policy will record the date and time of when a user logs in and out of an endpoint.
Application Monitor | If this option is enabled, the policy will record the date, time, and user of all application loads or exits.
Run Winget Updates | If this option is enabled it will update all of the winget packages installed on the endpoint that have the Auto Update option enabled on the Winget module.  It will only update winget packages that have an active policy assigning the winget module to the endpoint.  The Winget modules do not need to be assigned to the same policy with this option enabled.  A single Winget update policy will handle all modules in any policy.
Winget Use Download Connections | If this option is enabled, Winget package installations will follow the max download connections on your endpoint as to not overwhelm your network while downloading packages.  This only applies to the Winget packages assigned to this policy.
Remote Access | If you have installed the Remote Access Addon, this will control how the remote access client is pushed out to your endpoints

* **NotConfigured** - Does not do anything with the remote access client
* **Disabled** - Removes the remote access client
* **Enabled** - Install the remote access client and keeps the id up to date
* **ForceReinstall** - Force a reinstallation of the remote access client

 | 
------|------------
Join Domain | If you are using Toec to join your computers to a domain, this will enable the domain join for the policy.  You must first set the domain credentials in **Admin Settings-> Toec -> General**
Domain OU | If you want to join the computer to a specific OU, it should be specified here, such as ```OU=testcomputers,DC=theopenem,DC=com``` , leave this blank to join to the default Computers container
Image Prep Cleanup | If you used Toec-Image-Prep to prepare your image, you'll need a policy to cleanup things such as the temporary desktop background, enable this option to do that.
Install Available Windows Updates | This option can be used to install all available updates from Microsoft or a SUS server. This differs from a Windows Update module because it installs all available updates, where as a Windows update module installs a specific update. The Windows Update module has no relation to this setting.

* **Disabled** - The policy does not install any windows updates.
* **MicrosoftSkipUpgrades** - The endpoint will reach out to Microsoft's update servers to install all available updates, skipping feature upgrades.
* **WsusSkipUpgrades** - The endpoint will reach out to the designated SUS server to install all approved updates, skipping feature upgrades.
* **Microsoft** - The endpoint will reach out to Microsoft's update servers to install all available updates, including feature upgrades.
* **Wsus** - The endpoint will reach out to the designated SUS server to install all approved updates, including feature upgrades.

#### Actions
Action | Description
------|------------
Update Policy | Updates the policy with any changes you have made
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Assigned Modules
The assigned modules page allows you to update, remove, and order the modules that are currently assigned to the policy.  Modules will run in the order of the Order column from lowest number to highest.  Negative numbers may be used.
A condition may also be specified for each individual module.  If a condition fails for any module, the policy is completed with the result of the condition failed action, unless the action is set to **GoToModule**, then the policy can continue by
specifying the order number of the module to goto if the condition fails.  When changing any of the options for a module, you must select the update button in that same row to apply the changes.


#### Actions
Action | Description
------|------------
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Available Modules
This page is used to add modules to the policy. Modules can be filtered by module name and module type. There is an additional filter to show modules that are not assigned to any policies. Modules can be added to policies more than once.


#### Actions
Action | Description
------|------------
Add Selected To Policy | Adds the selected modules to the policy
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />


## Usages
The usages page allows you quickly see which Computers, or Groups currently have the policy assigned to them.  Use the **Usage Type** drop down list to switch b/w Groups or Computers.


#### Actions
Action | Description
------|------------
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Client History
This page displays every endpoint the policy was run as well the user that policy ran under. It also shows the result of the policy.  The policy hash link will show you the JSON representation of the policy at the time it was run on the endpoint. Every time the policy is changed, the hash value is updated and new endpoints would show the new hash value.


#### Actions
Action | Description
------|------------
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Policy History
Displays the JSON representation of the policy as it has changed over time.
<br />
<br />

#### Actions
Action | Description
------|------------
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />


## Categories
Categories operate like tags and allow you to organize your policies and filter by them on the search page. Categories can be defined in Global Properties->Categories
#### Actions
Action | Description
------|------------
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />

## Export
The export page allows the policy to be exported and shared with other people. When exporting a policy, a name and description must be provided. Any special instructions should also be included as well as any other requirements for the policy. Exporting a policy, exports all policy settings and all modules assigned to that policy. Uploaded files are not exported, if special files are required, they should be noted in the requirements. When possible a module should use external files, so after it's imported the necessary files can automatically be downloaded.

#### Actions
Action | Description
------|------------
Export Policy | Exports the current policy
Archive Policy | Archives the current policy
Delete Policy | Permanently deletes the current policy
Activate Policy | Activates the current policy
Deactivate Policy | Deactivates the current policy
Pin Policy | Adds the current policy to the dashboard
Unpin Policy | Removes the current policy from the dashboard 

<br />
<br />