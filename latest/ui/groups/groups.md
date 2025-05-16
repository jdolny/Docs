# Groups
Groups are used to define sets of computers for policies to target.

<br />
<br />

## Search
The search page allows you to view and delete groups. The search page also has a toggle to **Show AD OUs**. If you are syncing with Active Directory, this will display all OUs in list format as an alternative to the nested view on 
the Active Directory OU Browser page.

<br />
Groups can be filtered by the group name and category

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes all of the selected groups

<br />
<br />

## New
The new page allows you to create a new group.

Field | Description
------|------------
Name | The name of the group, group names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Group Type | Specifies a static or dynamic group. Static groups are manually assigned computers while dynamic groups automatically and continuously update members based on criteria set on the criteria page.
Description | The description field is optional for you to give a short description for what the group is for.
Communication Server Cluster | Groups can be used to specify which client com servers a computer should communicate with for both Toec communication and imaging. The default value is to use the default com server cluster. Clusters can be configured in admin settings->Client Com Servers.  If a computer is a member of multiple groups with default clusters assigned, the group with the lowest endpoint priority or imaging priority will be used.
Prevent Shutdown | If this option is enabled, any computers in this group cannot be shutdown or rebooted from Theopenem. This is helpful to prevent accidentally turning off an important computer. If a computer is in a group with this option enabled, and someone accidentally adds the computer to a group that has a shutdown schedule, it will not be powered off. This also applies to the Actions menu to shutdown or reboot.

#### Actions
Action | Description
------|------------
Add Group | Creates the group with the options specified in the fields

<br />
<br />

## Active Directory OU Browser
This page allows you to view OU's that have been synced from Active Directory. Active Directory OU's behave like static groups but are on a separate page to make it easier to browse. Each OU can be clicked on to assign policies or view group members. Clicking on a shaded arrow next to the OU displays any available sub OU's. If the arrow is an empty outline it does not contain any sub OU's. The ldap sync can be setup from admin settings->LDAP.

> [!NOTE]
> The following additional pages are available after a group is added or when selecting the view button on a specific group from the search page.

<br />
<br />

## General
The General page allows you to update the general options for the group.  It shows the same options as the New page, with the exception of the following additional fields.

Field | Description
------|------------
Wake Up Schedule |  Groups can be used automatically power on computers based on a schedule you define. Schedules can be created in Global Properties->Schedules.
Shutdown Schedule | Groups can be used to automatically power off computers based on a schedule you define. Schedules can be created in Global Properties->Schedules.
Endpoint Priority | Used to help determine which Communication Server Cluster an endpoint will use if it is a member of multiple groups that use different clusters. The lower number priority takes precedence.

#### Actions
Action | Description
------|------------
Update Group | Updates the group with any changes you have made
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Assigned Policies
This page displays all policies that are currently assigned to the group. The results can be filtered by policy name. This page also allows you to set the order in which the
 policies run. Both negative and positive values can be used. Policies can also be removed from the group from this page.

#### Actions
Action | Description
------|------------
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />


## Available Policies
This page is used to add policies to the group. Policies can be filtered by policy name.

#### Actions
Action | Description
------|------------
Add Selected Policies | Adds the selected policies to the group
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Dynamic Criteria
This page is only available when the group type is set to dynamic. This is used to set the criteria for the group members. 
Criteria is based on any inventory collection value or custom inventory script value or custom attribute value. Each line must be started with and / or, except for the first line. 
If using the not operator(The NOT operator should probably not be used in most situations and will most likely be removed in a future update due to unexpected results), 
there can be only one and it must be first. A wildcard % can be used before or after the string to match. The Actions menu has option to test the criteria before saving it. 
Dynamic groups update themselves every 3 hours based on the Admin Settings->Task Scheduler->Cron Expression. You can update this value to be more or less often.

#### Actions
Action | Description
------|------------
Test Query | Tests the current query before it is saved
Save Dynamic Criteria | Saves the current query
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Current Group Members
This displays all computers that are currently part of the group. If the group is static, computers can be removed from the group. 
Dynamic groups and Active Directory OU's cannot have computers removed from this page.

#### Actions
Action | Description
------|------------
Remove Selected Computers | Removes the selected computers from the group
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Add Group Members
This page is only available when group type is set to static. This allows you to manually add computers to the group.

#### Actions
Action | Description
------|------------
Add Selected Computers | Adds the selected computers to the group
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Send Message
This page can be used to send a message to all the computers in the group. A message will only display if a user is logged into the computer. 
The message just needs a Title and the message itself. The timeout value is used to automatically close the message after a certain time period. 
The default is 0, meaning it will not automatically close. This value is in seconds.

#### Actions
Action | Description
------|------------
Send Message | Sends the message to all computers in the group
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Categories
Categories operate like tags and allow you to organize your groups and filter by them on the search page. Categories can be defined in Global Properties->Categories
#### Actions
Action | Description
------|------------
Update Group | Updates the current group with the selected categories
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Process Report
This feature will most likely be deprecated in a future release.  The process report page makes it easy to determine the most commonly used applications for a given set of computers. 
A report can be displayed by time spent with application open, or the count of the most opened applications. This report may take a long time to run.  A policy must first be setup to capture this info before it can be used.

#### Actions
Action | Description
------|------------
Run Query | Runs the report
Export to CSV | Exports the current report to CSV.
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />

## Image Settings
This page is used to define image settings for an entire groups of computers instead of doing it per computer.

Field | Description
------|------------
Image |  The image that is assigned to the group. Setting an image here will not overwrite an image that is set directly on the computer. The image that is set individually on a computer always has a higher priority.
Image Profile | The image profile to be used with the image
WinPE Module | The WinPE module that will be used when using the Image Via Toec Action
Proxy Bootloader | If Theopenem Proxy DHCP is being used, a specific bootloader can be specified for all group members, overriding the global values.
Imaging Priority | Used to help determine which Image to use if the computer is a member of multiple groups that have different images assigned. The lower number priority takes precedence.  It is also used to determine which com servers to use when multiple clusters are available.

#### Actions
Action | Description
------|------------
Update Settings | Updates the image settings for the group
Delete Group | Permanently deletes the current group
Clear Imaging Ids | Resets the Imaging Id for all computers in a group. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset. 
Pin Group | Adds the group to the current users' dashboard.
Unpin Group | Removes the group from the current users' dashboard.
Start Multicast Imaging | Starts a multicast session for all members of the group using the image defined in the group's Image Settings
Start Unicast Imaging | Starts a unicast session for all members of the group using the image defined in the group's Image Settings
Start Imaging Via Toec | Starts an image deployment using Toec for all member of the group using the image defined in the group's Image Settings
Force Checkin | Forces all computers in the group to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on all computers in the group without needing to wait for an inventory policy to run.
Reboot | Reboots all computers in the group.
Shutdown | Powers off all computers in the group.
Wakeup | Powers on all computers in the group, using WOL.

<br />
<br />