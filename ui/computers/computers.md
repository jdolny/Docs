# Computers
The computers page provides the ability to view and manage your endpoints.

<br />
<br />

## Search Active
An active computer is any computer that has Toec installed and is not archived.  The search page allows you to view, delete, and archive existing computers, When a computer is no longer needed, best practice is to archive the computer. 
<br />
The search bar will search for following attributes on the computer.
* Computer Name
* Serial Number
* Last Username
* GUID
* Installation Id
* UUID
* Last Known IP
* Custom inventory attributes

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected computers
Delete Selected | Permanently deletes all of the selected computers

<br />
<br />

## Search Image Only
The search image only page displays all computers that have been registered with Theopenem using the Client Imaging OS, but do not have Toec installed.
<br/>
Filtering Options Include: <br/>

* Search by computer name
* By category

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected computers
Delete Selected | Permanently deletes all of the selected computers

<br />
<br />

## Search All
The search all page displays every computer that Theopenem is aware of, regardless of it's status. The most common status to lookup on this page is pre-provisioned and archived.
<br/>
Filtering Options Include: <br/>

* Search by computer name
* By category
* By limit
* By status
* By state - The state filter is used for AD synced computers, the AD sync will sync disabled computers also. If a computer is not synced from Active Directory, it's state is always enabled.

#### Actions
Action | Description
------|------------
Archive Selected | Archives all of the selected computers
Delete Selected | Permanently deletes all of the selected computers

<br />
<br />

## Approval Requests
The approval requests page is related to the security settings, new computer provision approval required and Pre Provision Approval Required, found in 
Admin Settings->Security. If either of those settings are enabled, computers cannot be provisioned until someone manually approves them. 
When a client computer tries to provision itself, it will stop and create an approval request. This page is used to either approve or deny the request. 
After a computer is approved it will automatically complete the provision process. A report is emailed twice a day if any approvals are waiting.

#### Actions
Action | Description
------|------------
Approve Request | Approves the request and allows the computer to provision
Deny Request | Denies the request, the request will continue to come back though if computer is still active

<br />
<br />

## Reset Requests
This page is an additional security setting for those that demand the most security. The require reset approval security option can be found in Admin Settings->Security. 
If at any time a computer cannot communicate with the server because of a security feature discrepancy such as mismatched key, mismatched certificate, mismatched installation id, 
or computer name, the client computers will reset itself and try to reprovision. If the require reset approval setting is enabled, 
it must manually approved before the computer can reset and reprovision itself. After the reset request is approved, the computer will automatically reprovision itself. 
A report is emailed twice a day if any approvals are waiting.

#### Actions
Action | Description
------|------------
Approve Request | Approves the request and allows the computer to provision
Deny Request | Denies the request, the request will continue to come back though if computer is still active

<br />
<br />

## Create Pre-Provision
This page is used to create pre-provisioned computers. Enter the computer names, one per line, in the textbox and select add PreProvisions. 
Preprovisioned computers serve two purposes. First, it allows you to add computers before they are provisioned. This allows you to place computers in the proper groups 
ahead of time. Second, is for security. A security option is available that will not let computers provision unless they have been pre-provisioned. This option is 
available in Admin Settings->Security->PreProvision Required. If AD sync is used, all synced computers are added as pre-provisioned computers.

#### Actions
Action | Description
------|------------
Add PreProvisions | Adds the computers to Theopenem in a pre-provisioned state.

<br />
<br />

## Create Image Only
This page is used to create Image Only computers from the web interface instead of registering them from the imaging client.
<br>
To add a single computer: <br/>
Provide the computer name and mac address, then select **Actions -> Create Single Computer** <br/>
To add multiple computers: <br/>
Enter the computer names and mac addresses, one per line, in the following format:<br/>
computername,00:11:22:33:44:55 <br/>
then select **Actions -> Create Computers From List**

#### Actions
Action | Description
------|------------
Create Single Computer | Adds a single image only computer.
Create Computers From List | Adds all the image only computers from the list.

<br />
<br />

> [!NOTE]
> The following additional pages are available when selecting the view button on a specific computer from the search page.


## General
The general page displays information specific to the functionality of Theopenem and is mostly for informational purposes. There a few fields that can be modified.
<br/>
 * Name - If the computer is image only, then the name can be updated
 * Primary Imaging Mac - Can be used to manually update the mac address of the computer used when identifying the computer during imaging
 * Imaging Client Id - Can be used to manually update the imaging id of the comptuer used when identifying the computer during imaging
 * Remote Access WebRtc Status - If using the remote access feature and the client keeps disconnecting during screen sharing, disable this option.
 
#### Actions
Action | Description
------|------------
Update Computer | Apply the updates for any changes to fields mentioned above.
Archive Computer | Archives the computer
Delete Computer | Permanently deletes the computer
Clear Imaging Id | Resets the ImagingId for this computer. An imaging id is based on a computers physical hardware. If imaging a computer does not correctly identify itself , it probably needs it's id reset.
Deploy Image | Starts an image deployment task for the computer using it's effective image, defined in Image Settings.
Upload Image | Starts an image upload task for the computer using it's effective image, defined in Image Settings.
Deploy Image Via Toec | Start an image deployment task via Toec instead of a PXE boot or USB boot media, using the image defined in image settings and the winpe module defined in image settings.
Force Checkin | Forces the computer to checkin immediately, instead of waiting for the next checkin interval.
Collect Inventory | Immediately runs an inventory collection on the computer without needing to wait for an inventory policy to run.
Current Users | Displays any users that are currently logged into the computer. 
Status | Displays true if the client computer can be reached through through Toec.
Remote Control | If the Remote Access addon is installed, starts a remote control session for the computer.
Reboot | Reboots the computer.
Shutdown | Powers off the computer.
Wake Up | Powers on the computer, using WOL.
System Uptime | Displays the amount of time the computer has been powered on.
Get Service Log | Gets a copy of the Toec log from the computer.

<br />
<br />

## System Info
This page displays all of the system information collected from an inventory scan.

## Software
This page displays all of the software that is currently installed on the computer. This info is also collected during an inventory scan.

## Windows Updates
This page displays all Windows updates that have been available for this computer. It will also display if the update has been installed and when.

## Certificates
This page displays all of the certificates from the Personal, Trusted Root, and Trusted Intermediate stores for the computer. This info is collected during an inventory scan.

## Custom Inventory
Theopenem can be used to collect additional inventory information that is not part of the standard inventory collection. These inventory script module results will appear on this page.

## Image Settings
Allows you to set an image for the computer to deploy or upload. The effective image takes group membership into account. An image does not need to be assigned directly to a computer, it can be from a group.
This page also allows you to set a WinPE module if you want to image via Toec instead.  The effective image is the image that will be ultimately be used.  If you are using On demand imaging, there is no need to set
an image on this page as you will select manually during the imaging process.  Finally, if you wish to send a static IP address with the LIE PXE boot only, it can be set here.

## Imaging Logs
Displays the list of imaging logs for the computer for debugging purposes.

## Usages
This page displays any groups, policies, or modules the computer is assigned to.  It can be a helpful troubleshooting tool.

## Effective Policy
This page makes it easy to determine exactly which policies will run on that computer depending on the client action and com server. The policy is displayed in JSON format representing exactly what is sent to the client. 
It is important to note, this displays all policies that could run, the client makes the final decision on what to run based on the policy run history.

## Policy History
This page displays the results of all policies that have ran on the computer.

## User Login History
Displays the login / logout time of all users of the computer.

## Custom Attributes
Allows you to define custom attributes that can be used to track additional information. Examples might include, asset tag number, windows product key, computer building name or room, etc. 
Custom attributes can be defined in **Global Properties->Custom Attributes**.

## Comments
Allows you to add any comments to the computer. Once a comment is added, it cannot be deleted or modified. An example usage, could be to track repair history.

## Attachments
Allows you to add any files to the computer, for later viewing. An example usage could be a purchase order.

## Send Message
This page can be used to send a message to the computer. A message will only display if a user is logged into the computer. The message just needs a Title and the message itself. The timeout value is used to automatically close the message after a certain time period. The default is 0, meaning it will not automatically close. This value is in seconds.

## Process Report
The process report page makes it easy to determine the most commonly used applications for a computer. A report can be displayed by time spent with application open, or the count of the most opened applications. 
You can also view a report for all users. This report may take a long time to run if the time frame goes back to far.  This requires a Process Report policy to be configured to collect this information.

## Instant Module Runner
This page can be used to run individual modules on a computer without the need to create a policy.  The computer must be active at the time you run it.  It will only try 1 time when the Run Module button is selected.