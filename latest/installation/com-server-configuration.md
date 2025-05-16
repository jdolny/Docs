## Com Server Configuration
The final step in configuring Theopenem is to get the Com Server setup.  Remember that a com server stands as it's own web application.  All of your client computers will only contact this service for management and imaging capabilities.  
They will never communicate with the Toems-UI or Toems-API.  The com server was already installed when you installed Theopenem, now it just needs configured.

<br />
<br />

## 1. Create A Com Server

* Select **Admin Settings** from the Navigation menu
* Select **Client Com Servers** from the Sub Navigation menu
* Select **Add Com Server** from the Sub Navigation menu
* Give the com server a **name**, every Toec-API application is considered a com server, the name should be something that identifies the server it's on, such as theopenem-01_com1
* The URL is the URL for the Toec-API on this server, using it's ip address or fqdn, followed by port 8888 such as, ```http://192.168.56.100:8888/```
* The Local Storage Path should already be populated.
* Click **Actions**, click **Add Server**
* You should now see a new set of options in the sub menu, select **Imaging Settings**
* Enter the **ip address** of this server in the **upload interface address**, should be the same ip you used in the url
* Select **Actions**, then **Update Server**
* Select **multicast settings**, enter the same ip in the **interface ip address**
* Select **Actions**, then **Update Server**
* Select **tftp settings**, enter the same ip in the **interface ip address**
* Select **Actions, then Update Server**

<br/>
<br/>

## 2. Set The Default Com Server Cluster

* Select **Admin Settings** from the Navigation menu
* Select **Client Com Servers** from the Sub Navigation menu
* Select **Add Com Server Cluster**
* Give the cluster a **name**, such as Central
* Enable the **Default Cluster Option**
* **Check the box next to your Com Server** you created earlier, leaving all other options to default values
* Click **Actions**, click **Add Cluster**

<br />
<br />

## 3. Update Toec-API Web.config
* In **Windows File Explorer**, navigate to ```C:\Program Files\Theopenem\Toems-API```
* Right click on **Web.config**, select **Edit With Notepad++**
* Scroll to the bottom of the file to find the **<connectionStrings\>** section
* Find the line that begins with ```<add name="toems" connectionString=```
* Copy that entire line to your clipboard
* In **Windows File Explorer**, navigate to ```C:\Program Files\Theopenem\Toec-API```
* Right click on **Web.config**, select **Edit With Notepad++**
* Scroll to the bottom and find the line that says ```<!--Copy Connection String from Application Server(Toems-API Web.confg) Below This Line-->```
* Paste the connection string that you copied from the Toems-API web.config right below that line
* Go back to the **Toems-API Web.config** file(It should still be open in Notepad++) 
* Scroll to the bottom and find the line that begins with  **<add key="DbEncryptionKey"**
* **Copy** the value of the **DbEncryptionKey** and paste it in the *Toec-API web.config file, updating the **"updatethisvalue"** with the new value.
* Keep Notepad++ open.  Log back into Theopenem Web UI.  
* Select **Admin Settings**.  Select **Client Com Servers**.
* Click **View** on the **Com Server you created earlier**.
* Copy the **unique id** to your clipboard.
* Go back to Notepad++ and view the Toec-API web.config file.
* Find the line  **<add key="ComServerUniqueId"** and update the **"updatethisvalue"** to match the unique id you copied from the Com Server
* Save and close Notepad++

**A completed Toems-API web.config file should look something like this.**
![](/latest/images/toec-api_config.png)

<br />
<br />

## 4. Test Toec-API
Now is a good time to test the Toec-API to see if the com server and web.config file are correct.

* Open a web browser
* Navigate to http://server-ip:8888/Provision/VerifyDb replacing server-ip with your actual ip or FQDN.  Ex: **http://192.168.56.100:8888/Provision/VerifyDb**
* The page should respond with the number 60
* If this step was successful the Toec-API is running and can access the database.  If not, verify your web.config file looks correct.


















