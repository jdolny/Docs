# Imaging Tasks
<br/><br/>
## Active Unicasts
Displays all active upload and deploy tasks that have been started by the current user. Administrators see tasks created from all users. Each task can also be cancelled from this page.
<br/><br/>

## Active Multicasts
Displays all active multicast tasks that have been started by the current user. Administrators see tasks created from all users. Each multicast task can also be cancelled from this page.
<br/><br/>

## All Active Tasks
Displays all active tasks that have been started by the current user. Administrators see tasks created from all users. Individual tasks can also be cancelled from this page. 
Administrators have an extra action on this page called Cancel All Tasks available from the Actions menu. This can be useful to clean things up. It clears all multicast processes, database entries, and boot files for all tasks.
<br/><br/>

## Unregistered On Demand Tasks
Displays all active tasks with an unregistered computer. If an on demand task is started with a registered computer, it is not displayed here. That is displayed in active unicasts page.
<br/><br/>

## Start On Demand Multicasts
On Demand multicast is a way to quickly start a multicast without needing to put computers into a group.  Fill out the fields and select Start Multicast from Actions menu then boot each client computer into On Demand Mode 
and select multicast. Finally select the corresponding session name to join. After you have connected all the clients simply press Enter on any client to start the multicast.

Field | Description
------|------------
Session Name | A name for the session that will appear on the client imaging console
Image | The image that will be deployed
Image Profile | The image profile to be used 
Client Count | Optional, If this is filled in, the session will auto start when that number of clients have connected.
Com Server | The server that will be used to send the multicast.

