# MariaDB / MySQL Database Setup
This section is only for user’s that have selected MariaDB / MySQL as their RDBMS.  If you have already setup MS SQL Server, continue on to the [database firewall section](/getting-started/database-firewall).  Some 
users may not be familiar with MariaDB, this guide will cover installation as well as setup.  If you will be using an existing MariaDB / MySQL installation, 
you can skip to [section 5](/getting-started/database-mariadb/#5-enter-the-following-sql-commands-and-replace-your-password-here-with-a-password-of-your-choosing).

###### 1.  Download MariaDB 
* Download [MariaDB 10.3.12-GA here](https://downloads.mariadb.com/MariaDB/mariadb-10.3.12/winx64-packages/mariadb-10.3.12-winx64.msi) or visit https://mariadb.com/downloads

---

###### 2.  Run the MariaDB MSI, continue through prompts accepting all default values until you reach the root password page
* Provide a password for the root account, this account will have full access to the database server, make it a strong one, Click Next
* Continue through the remaining prompts accepting all default values until installation is finished

!!! success "Continue filling in the Server Topology Worksheet under Database Server.  Fill in the Database Root/SA Password now."

 [![](https://theopenem.com/wp-content/uploads/2018/11/mdb-02.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/mdb-02.jpg)

---

###### 3.  Open a cmd prompt as administrator, change to MariaDB directory with the following command, this path might be different on different MariaDB versions
	cd "c:\Program Files\MariaDB 10.3\bin"

---

###### 4.  Still in cmd prompt, load the sql shell.  Enter the root password from section 2 when prompted
	
	mysql.exe -u root -p
  
---

###### 5.  Enter the following SQL commands, and replace **your-password-here** with a password of your choosing
	
	create database theopenem;
	create user 'theopenem_db_user'@'%' identified by 'your-password-here';
	grant all privileges on theopenem.* to 'theopenem_db_user'@'%';
	flush privileges;
	quit

!!! success "Continue filling in the Server Topology Worksheet under Database Server.  Fill in the Database Name, Database Username, and Database Password."
---

###### 6.  Locate the mysql.sql file from the Theopenem-1.1.0 package that was downloaded in the [Install Toems Web Applications Section](/getting-started/install-webapps)
  * Copy the mysql.sql file to c:\
  * Back in cmd prompt run the following to create the database tables, enter the root password when prompted:

&nbsp;

	mysql.exe --user=root --password --database=theopenem --execute="source c:\mysql.sql" -v

---

!!! success "This concludes the Setup Database if you have selected MariaDB / MySQL Server. Check this off of your Installation checklist now. "
