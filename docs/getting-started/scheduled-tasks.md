# Create Scheduled Task

!!! info "This section is only performed on the server that has the Toems-API Server Role set as primary.  If you remember, this role was defined in the Toems-API Web.config file."

Theopenem has a series of tasks that run at various time intervals.  This list can be found in Admin Settings->Task Scheduler.  These tasks are all initiated 
from within the Toems-API web application as long as it hasn’t gone to sleep.  The problem is that the Toems-API is only used when someone logs into the Toems-UI.  This 
means that the Toems-API is a very low traffic application and most of the time will be asleep preventing the Task Scheduler from running.  This section will setup a Windows Task 
to keep the Toems-API awake.

###### 1. Create A Local User To Run The Task
* Go to start or run and enter ```lusrmgr.msc```
* Right click on Users and select New User  
[![](https://theopenem.com/wp-content/uploads/2018/11/user-01.jpg)](https://theopenem.com/wp-content/uploads/2018/11/user-01.jpg)

* Enter ```toemskeepalive``` for the User name:
* Create a Password for the user
* Uncheck User must change password at next logon
* Check User cannot change password
* Check Password never expires
* Click Create  
[![](https://theopenem.com/wp-content/uploads/2018/11/user-02.jpg)](https://theopenem.com/wp-content/uploads/2018/11/user-02.jpg)
* Close any remaining dialog boxes  

---

###### 2. Give the User Batch Job Rights
* Go to start or run and enter ```secpol.msc```
* Expand Local Policies and Select User Rights Assignment
* In the Window on the right, scroll to the bottom and find Log on as a batch job, double click it
[![](https://theopenem.com/wp-content/uploads/2018/11/user-03.jpg)](https://theopenem.com/wp-content/uploads/2018/11/user-03.jpg)
* Click Add User or Group
* Ensure the location is set to the local computer and not the domain
* Enter toemskeepalive in the object names box, click Ok
[![](https://theopenem.com/wp-content/uploads/2018/11/user-03.jpg)](https://theopenem.com/wp-content/uploads/2018/11/user-03.jpg)
* Click Ok on any remaining dialog boxes

---

###### 3. Create Windows Scheduled Task
* Open the Windows Task Scheduler
* Right click on Task Scheduler (Local), select Import Task
[![](https://theopenem.com/wp-content/uploads/2018/11/task-01.jpg)](https://theopenem.com/wp-content/uploads/2018/11/task-01.jpg)
* Navigate to the Theopenem-1.1.0 folder you extracted back in the Install Toems Web Applications Section
* Select the Toems-API Keepalive.xml file, click Open
* On the General Tab, Click Change User or Group
* Enter toemskeepalive in the object names box, remember to change the location to local, click Ok
* Change the radio button to Run whether user is logged on or not
* Check the box for Do not store password
* Click OK, enter the toemskeepalive password when prompted

---

!!! success "This Concludes the Scheduled Tasks. Check this off of your Installation checklist now."