# Web.config Revisited
Now that everything in Theopenem is configured, there are some final changes to make to the web.config files.

###### 1. Update Toec-API web.config
* Open your text as editor as administrator
* Open the file **c:\inetpub\wwwroot\theopenem\Toec-API\Web.config**
* Scroll to the bottom of the file to find the **<appSettings\>** section
* Update the **LocalStoragePath** value to the directory you created back in the Create Storage Directory topic
* Save and close the file

!!! tip "If you have been filling out the Server Topology Worksheet this would be the Local Storage Path of Application Server 1."

---

###### 2. Update Toems-API web.config
* Open your text editor as administrator
* Open the file **c:\inetpub\wwwroot\theopenem\Toems-API\Web.config**
* Scroll to the bottom of the file to find the **<appSettings\>** section
* Update the **LocalStoragePath** value to the directory you created back in the Create Storage Directory topic

!!! tip "If you have been filling out the Server Topology Worksheet this would be the Local Storage Path of Application Server 1."

* Update the **AllowCAGen** value to **false**

> Setting this value to false ensures no one accidentally generates new certificates in the Toems-UI, doing so would break all communications with all Toec agents

* Update the **AllowProvisionKeyGen** value to **false**

> Setting this value to false ensures no one accidentally generates a new provision key, doing so would break endpoint provisioning

* Update the **ServerRole** value to either **primary** or **secondary**

> If only 1 Theopenem server is being used, the role is always primary.  If multiple Theopenem servers are used, only a single server can be set as primary.

!!! success "This concludes Web.config Revisited.  Check this off of your Installation checklist now."

