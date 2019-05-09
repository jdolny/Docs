# Configure Theopenem
!!! info "The following steps are all done after logging into any Toems-UI, these steps are only completed on a single server."

The Toems-UI has built-in help for most of the pages.  If you need additional clarification on something on one of the pages, click the Orange Info Button in the top right corner.  
[![](https://theopenem.com/wp-content/uploads/2018/11/orangeI.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orangeI.jpg)

###### 1. Change Admin Password

* Select Users from the Navigation Menu
* Select View on toemsadmin
* Update the User Password and Confirm Password fields
* Select Actions then Update User
* Click Logout from the Navigation Menu
* Log in with the new password

---

###### 2. Set Provision Key

* Select Admin Settings from the Navigation menu
* Select Security from the Sub Navigation menu
* Click Actions, Click Generate Provision Key
* Click Actions, Click Update Security Settings

---

###### 3. Set Organization Name

* Select Admin Settings from the Navigation menu
* Select Server from the Sub Navigation menu
* Fill in the name of your organization in the Organization field
* Click Actions, click Update Server Settings

---

###### 4. Set The Default Com Server Cluster

* Select Admin Settings from the Navigation menu
* Select Client Com Servers from the Sub Navigation menu
* Select Add Com Server from the Sub Navigation menu
* Give the com server a name, every Toec-API application is considered a com server, the name should be something that identifies the server it’s on, such as theopenem-01_com1
* The URL is the URL for the Toec-API on this server, using it’s FQDN, such as, ```http://theopenem-01.theopenem.com:8888/``` 

!!! tip "If you have been filling out the Server Topology Worksheet this would be the Server FQDN of Application Server 1 plus the port of the Toec-API role."

* Click Actions, click Add Server

!!! tip "If you are using more than 1 Toec-API, repeat the steps above to add all additional Com Servers"

* Select Admin Settings from the Navigation menu
* Select Client Com Servers from the Sub Navigation menu
* Select Add Com Server Cluster
* Give the cluster a name
* Enable the Default Cluster Option
* Check the box next to each Com Server you Added leaving the Role set to Active
* Click Actions, click Add Cluster

---

###### 5. Setup SMTP Server

* Select E-mail from the Sub Navigation menu
* Enable the Mail Enabled option
* Fill out the form with you SMTP server settings
* Click Actions, click Update E-mail Settings

---

###### 6. LDAP Setup

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

###### 7. Set the Storage Location

> If you are using a single Theopenem server with Toec-API and Toems-API installed on the same server:

* Select Admin Settings from the Navigation Menu
* Select Storage Location from the Sub Navigation Menu
* Set the Storage Type to Local
* Enter the local storage path that you created back in the Create Storage Directory Docs

!!! tip "If you have been filling out the Server Topology Worksheet this would be the Local Storage Path of Application Server 1."

* Click Actions, click Update Storage Settings

<br>

> If you are using multiple Theopenem servers with Toec-API and Toems-API installed on more than 1 server.

* You must first setup a file share on a remote server.  This must be an SMB share and can be on any device that supports SMB.  A user must be setup on that share with Read / Write privileges.  This share cannot be on any Theopenem server.
* Select Admin Settings from the Navigation Menu
* Select Storage Location from the Sub Navigation Menu
* Set the Storage Type to SMB
* Enter the Storage Path in UNC format, such as, \\\myfileserver\theopenem_share
* Enter the Username for the user that is used to connect to the share
* Enter the Password for the user that is used to connect to the share
* Enter the Domain for the user that is used to connect to the share, if applicable
* Click Actions, click Update Storage Settings


!!! success "Continue filling in the Server Topology Worksheet, fill in all file share information now"

---

###### 8. Generate Certificates

* Select Admin Settings from the Navigation Menu
* Select Certificates from the Sub Navigation Menu
* Click Actions, click Generate Certificates

---

!!! success "This concludes Configure Theopenem.  Check this off of your Installation checklist now."