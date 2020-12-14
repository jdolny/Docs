# Update Theopenem Web.config Files

###### 1.  Update Toems-UI Web.config
* In Windows File Explorer, navigate to C:\Program Files\Theopenem\Toems-UI
* Right click on **Web.config**, select **Edit With Notepad++**
* Scroll to the bottom of the file to find the **<appSettings\>** section
* Change the value for **ServerName** to anything you want to identify this server.  When multiple servers are used, this is displayed in the UI to show which server you are 
connected to.
* Leave the value for **ApplicationApiUrl** alone.  This value is always relative to your Toems-UI server.  If you installed the Toems-API and Toems-UI on 
the same server the value should always be ```http://localhost:8080```.  This value tells the Toems-UI(frontend) where to find the Toems-API(backend).
* Change the value for **UploadApiUrl** to include your server's ip address.  Replace the letters "fqdn" with the ip or the actual FQDN.  Example ```http://toems-01.theopenem.com:8080/``` or ```http://192.168.56.100:8080```.


> The **UploadApiUrl** value is strictly used for uploading files to Theopenem through the UI.  Typically when browsing the UI, your browser connects to the 
Toems-UI application and the Toems-UI connects to the Toems-API, with the exception of uploading files.  When uploading a file through the Toems-UI, your browser will 
connect directly to the Toems-API, skipping the Toems-UI application.  If you are having issues uploading files, it is most likely because this value is incorrect.

* Save and close the file

A completed Toems-UI web.config file should look something like this.


[![](https://theopenem.com/wp-content/uploads/2020/12/toems-ui_config.png)](https://theopenem.com/wp-content/uploads/2020/12/toems-ui_config.png)
---

###### 2.  Update Toems-API Web.config

* In Windows File Explorer, navigate to C:\Program Files\Theopenem\Toems-API
* Right click on **Web.config**, select **Edit With Notepad++**
* Scroll to the bottom of the file to find the **<appSettings\>** section
* Change the value for **AllowCAGen** to **false**
* Change the value for **AllowProvisionKeygen** to **false**
* Find the line that begins with <add name="toems" connectionString=
* Copy that entire line to your clipboard
* Save the file, but leave it open

A completed Toems-API web.config file should look something like this.


[![](https://theopenem.com/wp-content/uploads/2020/12/toems-api_config.png)](https://theopenem.com/wp-content/uploads/2020/12/toems-api_config.png)
---

###### 3.  Update Toec-API Web.config
* In Windows File Explorer, navigate to C:\Program Files\Theopenem\Toec-API
* Right click on **Web.config**, select **Edit With Notepad++**
* Scroll to the bottom and find the line that says <!--Copy Connection String from Application Server(Toems-API Web.confg) Below This Line-->
* Paste the connection string that you copied from the Toems-API web.config right below that line
* Go back to the Toems-API Web.config file(It should still be open in Notepad++) 
* Scroll to the bottom and find the line that begins with  <add key="DbEncryptionKey"
* Copy the value of the DbEncryption Key and paste it in the Toec-UI web.config file, updating the "updatethisvalue" with the new value.
* Keep Notepad++ open.  Log back into Theopenem web.  
* Select Admin Settings.  Select Client Com Servers.
* Click View on the Com Server you created earlier.
* Copy the unique id to your clipboard.
* Go back to Notepad++ and view the Toec-API web.config file.
* Find the line  <add key="ComServerUniqueId" and update the "updatethisvalue" to match the unique id you copied from the Com Server
* Save and close Notepad++

A completed Toems-API web.config file should look something like this.


[![](https://theopenem.com/wp-content/uploads/2020/12/toec-api_config.png)](https://theopenem.com/wp-content/uploads/2020/12/toec-api_config.png)
















