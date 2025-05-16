## Installing Toec
This guide will demonstrate how to generate the Toec installer as well as go over a few different options to install / deploy the client.
<br/>
<br/>

## Generate The Toec Installer
The last component that is needed to manage your endpoints, is the client agent, or Toec.  It must be installed on each endpoint you want to manage, but first we need to create it.

* Login to the **Toems web interface**
* Select **Admin Settings** from the Navigation menu
* Select **Toec** from the Sub Navigation menu
* Click the **Actions** button
* Select **Export Client Msi 64-bit**
* When prompted, **save the file somewhere**
* Click the **Actions** button
* Select **Export Client Msi 32-bit**
* When prompted, **save the file somewhere**

> [!Warning]
> You now have the Toec installers for both 32 and 64 bit OS's.  These installers are specific to your environment.  They have your certificates, com servers, and provision keys embedded into them.
> If you change your certificates, provision key or com server url, you will need to generate new Toec installers.


<br />
<br />

## Install Toec Via GUI / Cmd / Powershell
Now that the Toec MSI has been created, we can begin installing it to some test clients.  The installer is fully automated and can be installed from a gui simply by running the MSI or silently from cmd or powershell.

To install silently just pass the /q flag.
&nbsp;	

	Toec-1.5.4-x64.msi /q

> [!WARNING]
> If you are installing silently via cmd / powershell, the window must be elevated.  It will not prompt you for credentials. 

<br />
<br />

## Install Toec Via A Toec Deployment Job
Theopenem provides a simple method to deploy the Toec client to your computers within your network.  This is setup through the Toems Web UI.  To set this up:
1. Goto **Admin Settings->Toec->Create Target List**
2. Supply a **Name** for the list
3. Select the **List Type**:
 * **CustomList** - Manually type in a list of computer names or ip addresses in the box below, 1 per line
 * **AdOU** - If you have enabled LDAP integration, place a check in each box of each OU that contains the computers you want to deploy to
 * **AdGroup** - If you have enabled LDAP integration, place a check in each active directory group that contains the computers you want to deploy to
4. Select **Actions** then **Create Target List**
5. Select **Create Deploy Job** from the navigation menu on the left
6. Give the job a **Name**
7. Provide a **username** that has admin access to the group of computers in your target list. (Do not include the domain)
8. Provide the **password** for the user in step 7
9. Provide the **netbios** name of the domain for the user
10. Leave the job type and Job Mode to their default values
11. Select the **target list** you created in step 2 for the Target List dropdown menu
12. Set the **job** to **enabled**
13. Select **Actions** then **Create Deploy Job**
14. This job will now run in the background deploying Toec to your target list.  You may navigate away from this page.

<br />
<br />

## Additional Toec Options

#### Advanced Installation Arguments
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

<br/>

#### Command Line Options
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


