# Server Installation
This server installation guide will provide a complete walk through for the setup of Theopenem server (Toems) components.  These components include the **Toems-UI**, the **Toems-API**, 
the **Toec-API**, and **database**.
  The installation of the endpoint agent (Toec) will be covered in the Client Installation Tutorial.  If you have not yet read the [Welcome Introduction](/), please read it before 
  continuing. 
	
The installation process is mostly automated with the MSI.  The entire process should take about 20 minutes for you to complete.

# Prerequisites
- Install .NET 4.8.  
.NET 4.8 can be [downloaded here](https://dotnet.microsoft.com/download/thank-you/net48).  .NET 4.8.1 is also compatible.  .NET 5.0 and greater are not compatible.  They are fine if they are installed, 
but they will not serve as a substitute for .NET 4.8.x.
- Assign your server a static ip address

# Install Toems Web Applications

###### 1. Download the latest version of Theopenem from https://theopenem.com/downloads

###### 2. Run the installer
Most users should leave all of the default options selected during installation.  When asked for a local storage path, remember the location as you will need to enter that information in the web interface after installation.

###### 3. The Web Applications should now be installed.

# Configure Theopenem

!> "Each step below must be completed and in this order unless "optional" is specified next to it.

The Toems-UI has built-in help for most of the pages.  If you need additional clarification on something on one of the pages, click the Orange Info Button in the top right corner.  
[![](https://theopenem.com/wp-content/uploads/2018/11/orangeI.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orangeI.jpg)

###### 1. Login To Toems

* Toems should be accessible from any device on your network by entering the server's ip in your web browser.
* **Ex: http://192.168.56.100**
* The default admin username and password is **toemsadmin** for both fields.

---

###### 2. Change Admin Password (This must be done first or some functions of Theopenem will not work.)

* Select Users from the Navigation Menu
* Select View on toemsadmin
* Update the User Password and Confirm Password fields
* Select Actions then Update User
* Click Logout from the Navigation Menu
* Log in with the new password

---

###### 3. Set Organization Name

* Select Admin Settings from the Navigation menu
* Select Server from the Sub Navigation menu
* Fill in the name of your organization in the Organization field
* Click Actions, click Update Server Settings

---

###### 4. Set the Storage Location

* Select Admin Settings from the Navigation Menu
* Select Storage Location from the Sub Navigation Menu
* Set the Storage Type to Local
* Enter the local storage path that you specified during the installation of Theopenem.
* Click Actions, click Update Storage Settings

---

###### 5. Create A Com Server

* Select Admin Settings from the Navigation menu
* Select Client Com Servers from the Sub Navigation menu
* Select Add Com Server from the Sub Navigation menu
* Give the com server a name, every Toec-API application is considered a com server, the name should be something that identifies the server it’s on, such as theopenem-01_com1
* The URL is the URL for the Toec-API on this server, using it’s ip address, followed by port 8888 such as, ```http://192.168.56.100:8888/```
* The Local Storage Path should already be populated.
* Click Actions, click Add Server
* You should now see a new set of options in the sub menu, select Imaging Settings
* Enter the ip address of this server in the upload interface address, should be the same ip you used in the url
* Select Actions, then Update Server
* Select multicast settings, enter the same ip in the interface ip address
* Select Actions, then Update Server
* Select tftp settings, enter the same ip in the interface ip address
* Select Actions, then Update Server

---

###### 6. Set The Default Com Server Cluster

* Select Admin Settings from the Navigation menu
* Select Client Com Servers from the Sub Navigation menu
* Select Add Com Server Cluster
* Give the cluster a name, such as Central
* Enable the Default Cluster Option
* Check the box next to your Com Server you created earlier, leaving all other options to default values
* Click Actions, click Add Cluster

---

###### 7. Set Provision Key And Imaging Token

* Select Admin Settings from the Navigation menu
* Select Security from the Sub Navigation menu
* Click Actions, Click Generate Provision Key
* Click Actions, Click Generate Imaging Token
* Click Actions, Click Update Security Settings

---

###### 8. Generate Certificates

* Select Admin Settings from the Navigation Menu
* Select Certificates from the Sub Navigation Menu
* Click Actions, click Generate Certificates

---


###### 9. Setup SMTP Server (Optional, but recommended)

* Select E-mail from the Sub Navigation menu
* Enable the Mail Enabled option
* Fill out the form with you SMTP server settings
* Click Actions, click Update E-mail Settings

---

###### 6. LDAP Setup (Optional, but recommended)

* Select Admin Settings from the Navigation menu
* Select Security from Sub Navigation menu
* Enable LDAP Integration
* Click Actions, click Update Security Settings
* Select Admin Settings from the Navigation menu
* Select LDAP from the Sub Navigation menu
* Fill in the form with your LDAP specifications
* Click Actions, click Update LDAP settings
* Click Actions, Test AD Bind, to verify settings are correct

---


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


?> The **UploadApiUrl** value is strictly used for uploading files to Theopenem through the UI.  Typically when browsing the UI, your browser connects to the 
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


# Test Toec-API
Now is a good time to test the Toec-API to see if the com server and web.config file are correct.

###### 1.  Test Toec-API (Client connections)
* Open a web browser
* Navigate to http://server-ip:8888/Provision/VerifyDb replacing server-ip with your actual ip.  Ex: **http://192.168.56.100:8888/Provision/VerifyDb**
* The page should respond with the number 60
* If this step was successful the Toec-API is running and can access the database

---


# Install Certificates
The certificates are used for identification, encryption, and signing with your endpoints.  The CA and intermediate need to be imported into the Windows Certificate Store
on each Theopenem server.

###### 1. Export Certificates from Toems-UI
* Login to the Toems-UI from the server itself, do not do this remotely, these certificates are being installed on the Application Server itself, not an end user’s PC.
* Select Admin Settings from the Navigation Menu
* Select Certificates from the Sub Navigation Menu
* Find the certificate with the Type Authority and click Export
* Save the File when prompted
* Locate the file that was just downloaded and rename it to toems-ca
* Find the certificate with the Type Intermediate and click Export
* Save the File when prompted
* Locate the file that was just downloaded and rename it to toems-intermediate
* You should now have the 2 certificates saved on the local server
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-01.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-01.jpg)

---

###### 2. Install Certificates in the Local Certificate Store
* Double click on the toems-ca file, select Install Certificate
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-02.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-02.jpg)
* Select Local Machine, click Next
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-03.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-03.jpg)
* Select Place all certificates in the following store, click Browse, select Trusted Root Certificate Authorities, click OK, then Next, then Finish
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-04.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-04.jpg)
* Perform the previous 3 steps on the toems-intermediate certificate, this time when selecting the location to store the cert, select Intermediate Certification Authorities
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-05.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-05.jpg)


?> "This completes the installation of Toems, or the server components.  Up next we will begin to address the client installation or Toec."












