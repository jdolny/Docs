# Install Toems Web Applications

###### 1. Download the latest version of Theopenem from https://theopenem.com/downloads


---

###### 2. Verify the Sha256 Hash of the zip file
* Open powershell
* Enter Get-FileHash [theopenem zip location]

!!! info "Example"
	```powershell
	Get-FileHash c:\users\username\downloads\Theopenem-1.1.0.zip
	```

* Visit https://github.com/theopenem/Sha256Values to get the correct hash value for your version.  If the hash values do not match, please stop the installation and 
contact support@theopenem.com

---

###### 3. **Extract** the zip contents **to your desktop**
You should now have a folder on you desktop named Theopenem-1.1.0

---

###### 4. Open Theopenem-1.1.0 folder and **copy** the subfolder **theopenem** into the **IIS wwwroot**.
On a default Windows Server Installation, this directory is located at ```c:\inetpub\wwwroot\```. Your folder structure should now look like ```c:\inetpub\wwwroot\theopenem```, 
inside this folder should be three sub directories.  

	Toems-UI
	Toems-API
	Toec-API

Those 3 folders represent the three different web applications needed to run Theopenem.  If this specific server is not going to run all 3 applications, you should delete 
the extra applications now

---

!!! success "Continue filling in the Server Topology Worksheet under Application Server 1.  Check the appropriate roles this server will provide."

###### 5. Open **IIS Manager**, Go to **start or run** and enter **inetmgr**

---

!!! danger "This next step assumes no other web applications are running on this server, deleting the default web site could delete any existing web applications."

###### 6. Expand the server name, expand sites, right click on **Default Web Site**, select **remove**

  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step01.jpg){: style="height:400px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step01.jpg)

---

###### 7. **Right click** on **Sites**, select **Add Website**

  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step02.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step02.jpg)

---

###### 8. When the Add Website Form opens, enter the following values:

  |attribute|value|
  |---------|-----|
  |**Site Name**|Toems-UI|
  |**Physical Path**|c:\inetpub\wwwroot\theopenem\Toems-UI|
  
  Leave all other values as default and **click OK**
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step03.jpg){: style="height:300px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step03.jpg)

---

###### 8. Once again, **right click** on **Sites**, select **Add Website** with the following values:

  |attribute|value|
  |---------|-----|
  |**Site Name**|Toems-API|
  |**Physical Path**|c:\inetpub\wwwroot\theopenem\Toems-API|
  |**Port**|8080|
  
  Leave all other values as default and **click OK**
  
---

###### 9. One last time, **right click** on **Sites**, select **Add Website** with the following values:

  |attribute|value|
  |---------|-----|
  |**Site Name**|Toec-API|
  |**Physical Path**|c:\inetpub\wwwroot\theopenem\Toec-API|
  |**Port**|8888|
  
  Leave all other values as default and **click OK**
  
---

###### 10. **Right click** on **Toems-UI**, select **Manage Website**, select **Advanced Settings**
 
  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step04.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step04.jpg)

---

###### 11. Change **Preload Enabled** to **True**
 
  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step05.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step05.jpg)

---

###### 12. Apply the previous Preload step to both the **Toems-API** and **Toec-API** Websites
 
---

###### 13. Select **Application Pools** from the menu on the left, **right click Toec-API**, select **Advanced Settings**
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step06.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step06.jpg)

---

###### 14. Change the following values
  
  |attribute|value|
  |---------|-----|
  |**Start Mode**|Always Running|
  |**Load User Profile**|True|
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/iis-step07.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/iis-step07.jpg)

---

###### 15. Apply the previous Start Mode / Load User Profile step to both the **Toems-API** and **Toec-API** Application Pools
 
---

!!! success "This concludes Install Toems Web Applications.  Check this off of your Installation checklist now. "


