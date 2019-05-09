# Create Storage Directory And Set Permissions
A local file storage folder must be created to store all file uploads, external downloads, attachments, and Toec agent upgrade files.  If you are running Theopenem 
from a single server, these files will all go directly to this folder after upload from the Web UI.  If you are running multiple Theopenem servers, these files will 
instead first go to a file share and will then be replicated to each server’s local storage path.  Regardless if you are running a single Theopenem server or in a cluster, 
local storage path is always used.

!!! tip "Determine a local storage location"
	Think of the best place for this folder, it must be large enough to fit all of the software you will be deploying.  If you only have 1 drive, then at the root c:\ works fine.  Something such as c:\theopenem_local_storage is suggested.

###### 1. Create Local Storage Directory	
* Create the folder at the designated location now.  This example uses c:\theopenem_local_storage.

!!! success "Continue filling in the Server Topology Worksheet under Application Server 1.  Fill in the Local Storage Path."

* After the folder is created, Right click, select properties, then the Security tab, then Edit, then Add
[![](https://theopenem.com/wp-content/uploads/2018/11/fs-01.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/fs-01.jpg)
* Ensure that **From this location** says the **name of the server** and not the domain name, if so change it by clicking on Locations  
* Enter ```IIS AppPool\Toems-API;IIS AppPool\Toec-API``` click OK
[![](https://theopenem.com/wp-content/uploads/2018/11/fs-02.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/fs-02.jpg)
* Toec-API and Toems-API should now appear in the security list, select Toec-API and check the Modify Permission in the Allow column, do the same for Toems-API.  Click OK on any remaining dialog boxes.

---

###### 2. Set Web Application Log Folder Permissions
The following steps are required to give each web application permissions to write to the log file.  The steps are very similar to section 1.

* Navigate to **c:\inetpub\wwwroot\theopenem\Toec-API\private**
* **Right click on logs**, select **properties**, select the **Security tab**, select **Edit**, then **Add**
* Add the ```IIS AppPool\Toec-API``` user with **modify** permissions

<br>

* Navigate to **c:\inetpub\wwwroot\theopenem\Toems-API\private**
* **Right click on logs**, select **properties**, select the **Security tab**, select **Edit**, then **Add**
* Add the ```IIS AppPool\Toems-API``` user with **modify** permissions

<br>

* Navigate to **c:\inetpub\wwwroot\theopenem\Toems-UI\private**
* **Right click on logs**, select **properties**, select the **Security tab**, select **Edit**, then **Add**
* Add the ```IIS AppPool\Toems-UI``` user with **modify** permissions

---

!!! success "This concludes Create Storage Directory And Set Permissions.  Check this off of your Installation checklist now."
