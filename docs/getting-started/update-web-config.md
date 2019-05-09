# Update Theopenem Web.config Files
Each web application has a web.config file that must be updated before the application can be used.  It is highly recommended to use a good text editor, 
such as Notepad++ for editing these files.

###### 1.  Update Toems-UI Web.config
* Open your text as editor as administrator
* Open the file **c:\inetpub\wwwroot\theopenem\Toems-UI\Web.config**
* Scroll to the bottom of the file to find the **<appSettings\>** section
* Change the value for **ServerName** to anything you want to identify this server.  When multiple servers are used, this is displayed in the UI to show which server you are 
connected to.
* Change the value for **ApplicationApiUrl** to the URL for your Toems-API.  This value is always relative to your Toems-UI server.  If you installed the Toems-API and Toems-UI on 
the same server the value should always be ```http://localhost:8080```.  This value tells the Toems-UI(frontend) where to find the Toems-API(backend).
* Change the value for **UploadApiUrl** to the URL for your Toems-API for remote connections, in other words, the URL that can be used to for end users to communicate with the Toems-API.  This 
value is always relative to your Theopenem Administrators web browser.  This would typically be the FQDN of the server, and the port the API is running on, such as, ```http://toems-01.theopenem.com:8080/```.

!!! tip "If you have been filling out the Server Topology Worksheet, this is the FQDN of the Application Server 1 section with the port of the Toems-API role"

> The **UploadApiUrl** value is strictly used for uploading files to Theopenem through the UI.  Typically when browsing the UI, your browser connects to the 
Toems-UI application and the Toems-UI connects to the Toems-API, with the exception of uploading files.  When uploading a file through the Toems-UI, your browser will 
connect directly to the Toems-API, skipping the Toems-UI application.  If you are having issues uploading files, it is most likely because this value is incorrect.

* Save and close the file

---

###### 2.  Update Toems-API Web.config
* Open your text as editor as administrator
* Open the file **c:\inetpub\wwwroot\theopenem\Toems-API\Web.config**
* Scroll to the bottom of the file to find the **<connectionStrings\>** section.  

> The connection string is used to connect to the database.  An example for both MS SQL and MariaDB are provided in the file.  Uncomment the correct example for your 
database by removing the <!– before the example, and the –> after the example

!!! example "The commented MS SQL connection string looks like this"
	```xml
	<!-- Microsoft SQL Server EXAMPLE -->
	<!--
	<add name="toems" connectionString="Data Source=[server-name];Initial Catalog=theopenem;Integrated Security=False;User Id=[user];Password=[password];MultipleActiveResultSets=True" providerName="System.Data.SqlClient" />
	-->
	```

!!! example "After the comments are removed, it looks like this"
	```xml
	<!-- Microsoft SQL Server EXAMPLE -->
	<add name="toems" connectionString="Data Source=[server-name];Initial Catalog=theopenem;Integrated Security=False;User Id=[user];Password=[password];MultipleActiveResultSets=True" providerName="System.Data.SqlClient" />
	```

* Now that the connectionString is uncommented, it’s time to update it.  Change the **[server-name]** , **[user]** , and **[password]** values to the correct values, the brackets should be removed.

!!! tip "If you have been filling out the Server Topology Worksheet, the values needed above are the Database Name, Database Username, and Database Password from the Database Server Section"

!!! danger "Important, If you used any of the following special characters in the password, it must be changed to the corresponding Entity Name value"

	|Character|Description|Entity Name|
	|------|-----------|-----------|
	| |non-breaking space|```&nbsp;```|
	|<|less than|```&lt;```|
	|>|greater than|```&gt;```
	|&|ampersand|```&amp;```|
	|"|quote|```&quot;```|
	|'|apostrophe|```&apos;```|


!!! example "A final connectionString for MS SQL Server may look something like this"
	```xml
	<add name="toems" connectionString="Data Source=db01.theopenem.com;Initial Catalog=theopenem;Integrated Security=False;User Id=theopenem_db_login;Password=Ihjskessnkj;MultipleActiveResultSets=True" providerName="System.Data.SqlClient" />
	```
	
Or

!!! example "A final connectionString for MariaDB may look something like this"
	```xml
	<add name="toems" connectionString="Server=localhost;Port=3306;Database=theopenem;Uid=theopenem_db_user;Pwd=jjierjsneyy;" providerName="MySql.Data.MySqlClient" />
	```

<br>

* Scroll down to the **<appSettings\>** section
* Update the **DbEncryptionKey** value to a random string *(A guid from https://www.guidgen.com works nicely)*.  This value is used to encrypt sensitive data that is stored in the database.
* Save and close the file

!!! danger "The DbEncryptionKey value must be the same on all Toems-API and Toec-Api Applications"
	It is extremely important that you do not lose this key.  If the key is lost, Theopenem will fail to function, your data will be lost, and endpoints will not be able to check-in

!!! success "Continue filling in the Server Topology Worksheet, fill in the Application Server 1 Toems-API DbEncryptionKey"

---

###### 3.  Update Toec-API Web.config
* Open your text as editor as administrator
* Open the file **c:\inetpub\wwwroot\theopenem\Toec-API\Web.config**
* Scroll to the bottom of the file to find the **<connectionStrings\>** section
* Update the connection string to match the string you created for the Toems-API web.config in section 2
* Scroll down to the **<appSettings\>** section
* Update the DbEncryptionKey value to the same value that was used for the Toems-API web.config file in section 2

!!! tip " If you are filling in the Server Topology Worksheet, this is the Toems-API DbEncryptionKey from Application Server 1"

!!! success "Continue filling in the Server Topology Worksheet, fill in the Application Server 1 Toec-API DbEncryptionKey"

!!! success "This concludes Update Theopenem web.config Files.  Check this off of your Installation checklist now."















