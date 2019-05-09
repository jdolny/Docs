# Microsoft SQL Server Database Setup
This guide will walk you through setting up a new database for Theopenem, creating the necessary tables, and adding a user on Microsoft SQL Server.  This guide does not provide 
details on how to install Microsoft SQL Server. If you will instead be using MariaDB / MySQL, continue on to [this guide](/getting-started/database-mariadb).  

###### 1. Open SQL Server Management Studio and connect to the SQL Server that will house the Theopenem database
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-01.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-01.jpg)

---

###### 2. Right click on Databases and select New Database
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-02.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-02.jpg)

---

###### 3. Give the Database a name, such as theopenem, modify the Initial Size of the database and log file to 1000 MB, modify the Autogrowth setting to 500MB or more on both, click OK
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-03.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-03.jpg)

---

###### 4. Select File, Open, File, select the sqlserver.sql file that was in Theopenem-1.1.0 Package you downloaded earlier.
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-04.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-04.jpg)

---

###### 5. The script should be displayed in the query window.  Verify the Available Databases drop down displays theopenem and select Execute
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-05.jpg)](https://theopenem.com/wp-content/uploads/2018/11/mssql-05.jpg)

---

###### 6. On left side menu, expand Security, right click Logins, select New Login
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-06.jpg){: style="height:150px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-06.jpg)

---

###### 7. Select SQL Server authentication, enter a login name, such as theopenem_db_login, enter a password, uncheck the following boxes:

  |Uncheck|
  |-------|
  |Enforce Password Policy|
  |Enforce Password Expiration|
  |User must change password at next login|
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-07.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-07.jpg)

---

###### 8. Select the User Mapping Page, check the box for theopenem database on the top menu, check the box for db_owner on the bottom menu, click OK
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/mssql-08.jpg){: style="height:350px"}](https://theopenem.com/wp-content/uploads/2018/11/mssql-08.jpg)

---

!!!success "Continue filling in the Server Topology Worksheet under Database Server.  Fill in the Database Name, Database Username, and Database Password."

!!!success "This concludes the Setup Database if you have selected Microsoft SQL Server. Check this off of your Installation checklist now."











