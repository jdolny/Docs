# Client Installation (Toec)

Before client configuration / installation can begin.  It's important to understand some basic provisioning concepts.  Provisioning is the process of allowing an endpoint to be managed by Theopenem.  
This includes the exchange of certificates and encryption keys b/w the client and server.  This process is automated when the Toec Agent is installed, but there are some settings on the Server that should be addressed to ensure a smooth provisioning process.

## Active Directory Sync
Syncing with Active Directory is highly recommended but not required.  It is a read only one way sync from AD to Theopenem.  It will sync in Computer names and 
Organizational Unit names, servers are skipped.  The benefit of syncing in the Computers is to pre-provision them.  A pre-provisioned computer is added to Theopenem 
but cannot yet be managed until provisioning from the client completes.  When a computer is pre-provisioned, it can be assigned to groups with policies already defined, 
this way when an endpoint completes the provisioning process, it will automatically start running the necessary policies.  Syncing from AD also allows you to assign 
policies to your existing OU's, as another method of targeting groups of computers.  If you skipped over the LDAP setup during the server installation it's recommended 
to configure it now.

* Login to the ***Toems-UI***, select ***Admin Settings->Security***
* ***Enable*** the ***LDAP Integration*** if not already enabled
* Click ***Actions***, ***Update Security Settings***
* Select ***Admin Settings->LDAP***
* Fill out the ***LDAP form***, use the built-in help menu in the top right for more info on the fields
* Click ***Actions***, ***Update LDAP Settings***
* Click ***Actions***, ***Test AD Bind***, to verify the connection was successful
* Select ***Admin Settings->Task Scheduler***
* Find the ***LDAP Sync*** row and click ***Run Now***.  There is no visual confirmation when using the Run Now button.  By default this task will run every night at 1:00AM.  
Give the process 5-10 minutes to run, you can navigate away from the page.
* Select ***Computers->Search All***.  It should show all of the synchronized computers with a Provision Status of PreProvisioned.
* Select ***Groups->Active Directory OU Browser***.  You should see your Domain Directory Tree.

---


## Provisioning Security
There are a few security measures in place to regulate endpoint provisioning.  They are currently all on by default, but you may disable them.  The 
following options are available in ***Admin Settings->Security***.


* **Preprovision Required** – When this option is enabled, a computer will not be allowed to provision unless it has already been pre-provisioned.  If you are syncing from Active 
Directory, computers have already met this requirement when they were synced.  If you are not syncing from AD, pre-provisions may be manually added from Computers->Create Pre-Provision.
* **New Computer Provision Approval Required** – When this option is enabled, a Theopenem user must manually approve computers before they will be allowed to provision.  This 
setting does not apply to pre-provisioned computers since they have already been approved.  Provision approval requests will be displayed in Computers->Approval Requests when a 
new computer tries to provision for the first time.  This is where the user can approve or deny the request.  A report is emailed twice per day when endpoints are waiting for approval.
* **Preprovision Approval Required** – This setting is a combination of the previous two settings.  When this is enabled, a user must manually approve and endpoint’s provision request 
even if it has already been pre-provisioned.  The request are still approved from Computers->Approval Requests, and a report is still sent twice per day.

---

## Generate Toec Installer
The last component that is needed to manage your endpoints, is the client agent, or Toec.  It must be installed on each endpoint you want to manage, but first we need to create it.

* Login to the ***Toems web interface***
* Select ***Admin Settings*** from the Navigation menu
* Select ***Toec*** from the Sub Navigation menu
* Click the ***Actions*** button
* Select ***Export Client Msi 64-bit***
* When prompted, ***save the file somewhere***
* Click the ***Actions*** button
* Select ***Export Client Msi 32-bit***
* When prompted, ***save the file somewhere***

---

?> You now have the Toec installers for both 32 and 64 bit OS's.  These installers are specific to your environment.  They have your certificates, com servers, and provision keys embedded into them.
!> If you change your certificates or provision key, you will need to generate new Toec installers.

---

## Install Toec Via GUI / Cmd / Powershell
Now that the Toec MSI has been created, we can begin installing it to some test clients.  The installer is fully automated and be installed from a gui simply by running the MSI or silently from cmd or powershell.

To install silently just pass the /q flag.
&nbsp;	

	Toec-1.5.0-x64.msi /q

!> If you are installing silently via cmd / powershell, the window must be elevated.  It will not prompt you for credentials. 

---

## Additional Toec Options

#### 1. Advanced Installation Arguments
There are a few extra arguments that can be passed in during the installation of Toec, or embedded into the MST file.  Reinstalling 
the MSI with any of these options will also overwrite the current value without changing anything that is not specified.

* ```LOG_LEVEL``` – The default logging level of Toec is **INFO**.  To get more information, **DEBUG** can used. To get less information, **ERROR** can be used.  
<br>
* ```LOCAL_API_PORT``` – Toec listens on port **1415** by default for local requests only.  The Toec-UI application for user logins cannot talk directly to Toems, it instead 
uses the Toec Service on port 1415 as an intermediary for this.  
<br>
* ```USER_PORT_RANGE``` – The Toec-UI application loads at startup for each user that logs into the endpoint.  Each Toec-UI will receive a corresponding port to 
communicate with that instance.  The **default range is 9000-10000**.  
<br>
* ```RESET_DB``` – Used when reinstalling Toec.  By default, the existing database is still used when Toec is reinstalled.  Setting this value to true will clear the client 
database, treating the installation as if it were new.  This would cause the endpoint to provision again.

---

#### 2. Command Line Options
After Toec is installed, it can also be run from the command line to change options or help in debugging.  When using any of these commands, they must be run from an 
elevated cmd prompt and the service should be stopped.  Toec.exe is located in c:\program files\toec.
<br><br>

	Toec.exe --console
Starts Toec is console mode, displaying helpful debug info in the window.

<br>

	Toec.exe --version
Displays the current Toec version

<br>

	Toec.exe --logLevel [INFO|DEBUG|ERROR]
Updates the log level

<br>

	Toec.exe --resetFull
This resets Toec back to a new installation state, deleting all settings, certificates, installationId, and history.  This would cause the endpoint to 
provision again.  If you are having trouble with the endpoint, try the partial before the full reset.  A full reset may result in the loss of an existing relationship 
b/w the client and server.

<br>

	Toec.exe --resetPartial
This performs a partial reset on Toec.  History and installationId are not removed, everything else is reset.  This will also cause the endpoint to provision 
again.

<br>

	Toec.exe --resetKey [SERVER_KEY] [CA_THUMBPRINT]
Changes the server key and ca thumbprint for the endpoint.

<br>

	Toec.exe --prepareImage
If you want to install Toec before capturing an image of the computer.  You must run this prior to the last shutdown of the computer.  Failure to run this will cause each client's installation id to be the same, preventing Toec from working properly.

<br>

	Toec.exe --comServers [COM_SERVERS]
Updates the com servers for the endpoint with a comma seperated list of servers.


