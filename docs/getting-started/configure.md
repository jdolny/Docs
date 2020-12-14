# Configure Theopenem

!!! danger "Each step below must be completed and in this order unless "optional" is specified next to it."

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
