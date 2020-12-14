# Toec Advanced Options

###### 1. Advanced Installation Arguments
There are a few extra arguments that can be passed in during the installation of Toec, or embedded into the MST file.  Reinstalling 
the MSI with any of these options will also overwrite the current value without changing anything that is not specified.

* ```LOG_LEVEL``` – The default logging level of Toec is **INFO**.  To get more information, **DEBUG** can used. T o get less information, **ERROR** can be used.  
<br>
* ```REMOTE_API_PORT``` – Specifies the port that Toec will listen on for push requests from Toems.  **The default value is 3913**.  Push requests are not required for 
Theopenem to function, but it does provide the following capabilities from the computer actions menu,  Current Users and Status.  Previously this port was used for all push
communications, but now with the move to web sockets, only the previously mentioned commands use it.  Eventually it will be removed completely and solely rely on web sockets.  
<br>
* ```LOCAL_API_PORT``` – Toec also listens on port **1415** by default for local requests only.  The Toec-UI application for user logins cannot talk directly to Toems, it instead 
uses the Toec Service on port 1415 as an intermediary for this.  
<br>
* ```USER_PORT_RANGE``` – The Toec-UI application loads at startup for each user that logs into the endpoint.  Each Toec-UI will receive a corresponding port to 
communicate with that instance.  The **default range is 9000-10000**.  
<br>
* ```REMOTE_ADDRESSES``` – When Toec is installed, it automatically creates a firewall exception for port 3913 to allow inbound requests.  By default this exception 
is allowed for any ip address.  If you want to limit the IP’s that the exception is for, they can be specified in a comma separated list here.  Such as 192.168.1.10,192.168.1.11.  Be 
careful with this setting, if you input the wrong ip’s, your Toems IP changes, or you add an additional Toems Server, you may not be able to communicate with your endpoints until 
you update the exception.  
<br>
* ```SKIP_FIREWALL``` – When Toec is installed, it automatically creates a firewall exception for port 3913 to allow inbound requests.  If this argument is set to true, 
the exception will not be created.  
<br>
* ```RESET_DB``` – Used when reinstalling Toec.  By default, the existing database is still used when Toec is reinstalled.  Setting this value to true will clear the client 
database, treating the installation as if it were new.  This would cause the endpoint to provision again.

---

###### 2. Command Line Options
After Toec is installed, it can also be run from the command line to change options or help in debugging.  When using any of these commands, they must be run from an 
elevated cmd prompt and the service should be stopped.  Toec.exe is located in c:\program files\toec.  **The commands are case sensitive**.
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

	Toec.exe --prepareImage [SERVER_KEY] [CA_THUMBPRINT]
If you want to install Toec before capturing an image of the computer.  You must run this prior to the last shutdown of the computer.  Failure to run this will cause each client's installation id to be the same, preventing Toec from working properly.

<br>

	Toec.exe --comServers [COM_SERVERS]
Updates the com servers for the endpoint.


