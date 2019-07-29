# Creating Your First Policy
This last section is not required, but will provide you with a brief introduction on how to run some policies on your endpoints.  By this point you should have at least 1 or 2 
endpoints provisioned with Theopenem.  These can be seen from the Toems-UI from the Computers->Search Active page.  If you don’t see anything listed there yet, double 
check the Computers->Approval Request page to make sure nothing is waiting for approval.

###### 1. Create A Dynamic Group
There a typically a few policies that you would want to run on all computers.  These policies may include inventory tracking, user login tracking, and application usage 
tracking.  A dynamic group is a group that is always changing the group members based on criteria that is defined.  This first dynamic group will include all computers.

* Login to the Toems-UI
* Select **Groups->New**
* Provide a **name** such as ==All Computers==
* Set the **Group Type** to ==Dynamic==
* Provide a nice **description**.
* Leave all other options to their defaults
[![](https://theopenem.com/wp-content/uploads/2019/01/policy-step01.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2019/01/policy-step01.jpg)
* Click **Actions**, then **Add Group**
* Select **Dynamic Criteria** from the **Sub Navigation Menu**
* Change **Table** to ==Computer==, the **Field** to ==computer_name==, the **Operator** to ==like== , and the **Value** to ==%==, click **Add**
[![](https://theopenem.com/wp-content/uploads/2019/01/policy-step02.jpg){: style="height:100px"}](https://theopenem.com/wp-content/uploads/2019/01/policy-step02.jpg)
* Click **Actions**, then **Test Query**.  Should should see the list of all known computers.
* Click **Actions**, then **Save Dynamic Criteria**
* Your first group is complete.  By default, Dynamic Groups update themselves every 3 hours.  Saving the Dynamic Criteria again will also trigger the update.

---

###### 2. Create An Inventory Policy

* Select **Policies->New**
* In the **Name** field, enter ==Collect Inventory==
* In the **Description** field, enter ==Collect inventory on a weekly basis==.
* Change the **Frequency** to ==OncePerWeek==.
* Scroll down to **Collect Inventory**, change the drop down to ==Before==
* Scroll down to **Skip Server Logging Result**, ==enable== it.  We don’t really want a long history of inventory scans running every week clouding our logs.
* Click **Actions**, then **Add Policy**

---

###### 3. Create A Tracking Policy

* Select **Policies->New**
* In the **Name** field, enter ==Track Users and Applications==
* In the **Description** field, enter ==Starts the user login and application tracker each time the computer starts==.
* Change the **Trigger** to ==Startup==
* Leave the **Frequency** at ==Ongoing==
* Scroll down, ==Enable Login Tracker and Application Monitor==
* Skip the Server Logging Result once again.
* Click **Actions**, then **Add Policy**.

---

###### 4. Apply The Policies
In order for a Policy to take effect, it needs to be enabled and assigned to a group.

* Select **Policies->Search**
* Click **Activate** on each of the 2 policies listed
* Select **Groups->Search**
* Click **View** on the **All Computers Group**
* Click **Available Policies** from the **Sub Nav Menu**.
* **Check the box** for each of the Policies we just created.
* Click **Actions**, Add **Selected Policies**.

That completes the inventory policies.  Every computer that provisions with Theopenem will now do a weekly inventory scan as well as monitor 
application usage and user logins.  The inventory scan will run at the next check-in for you provisioned endpoints which is every 60 minutes by default.  The tracking 
policy only runs at startup, you will need to either reboot those endpoints or restart the Toec service to test it.

---

###### 5. Deploy A Software Application In MSI Format
For this example, we will create a new static group, targeting specific computers and then deploy 7-Zip.

* Select **Groups->New**
* Give the group a **name** such as ==Software Deployment Test Group==
* Leave the **Group Type** as ==Static==.
* Click **Actions**, **Add Group**
* Select **Add Group Members** from the **Sub Nav Menu**.
* **Check the box** next to **each computer** to add to the group.
* Click **Actions**, **Add Selected Computers**.
* Select **Modules** from the **Navigation Menu**.
* Select **Software Modules**, Then **New**
* Enter ==7-Zip 18.06== for the **Name**
* Click **Actions**, **Add Module**
* Select **Upload Files** from the **Sub Nav Menu**
* **Download 7-Zip** from [this link](https://www.7-zip.org/a/7z1806-x64.msi)
* **Drop** the downloaded MSI into the **Drop Files Here box**, Click **Upload**
* Select **Policies->New** from the Navigation Menu
* Give the policy a **name** such as ==Install 7-Zip==
* Change the **Frequency** to ==OncePerComputer==
* Click **Actions**, **Add Policy**
* Select **Available Modules** from the **Sub Nav Menu**
* **Check the box** for **7-Zip 18.06**, Click **Actions**, **Add Selected To Policy**
* Click **Actions** then, **Activate Policy**
* Assign the Policy to the Software Deployment Test Group

The next time any of the computers in that group startup or check-in, 7-Zip will automatically be installed.

---

###### 6. Deploy A Software Application In Exe Format
An exe can be deployed as long as it support silent options.  This last example will silently deploy Firefox.  We’ll use a dynamic group to 
find computers that do not have firefox installed.  Finally we’ll introduce a new concept called external downloads.

* Select **Groups-> New** From the Navigation Menu
* For the **name**, enter ==Computers Missing Firefox==
* Change the **Group Type** to ==Dynamic==
* Click **Actions**, **Add Group**
* Select **Dynamic Criteria** from the **Sub Nav Menu**
* Change the **And/Or** dropdown to ==Not==, the **Table** to ==Application==, the **Field** to ==name==, the **Operator** to ==like==, and the **Value** to ==%firefox%== ,click **Add**  
[![](https://theopenem.com/wp-content/uploads/2019/01/policy-step03.jpg){: style="height:100px"}](https://theopenem.com/wp-content/uploads/2019/01/policy-step03.jpg)
* Click **Actions**, **Save Dynamic Criteria**
* Select **Modules->Command Modules->New** from the **Navigation menu**.
* For the **name** enter, ==Firefox 64.0.2==
* Click **Actions**, **Add Module**
* Select **External Files** from the **Sub Nav menu**
* Fill in a **File Name**, such as ==Firefox.exe==, it can be any name you like, it’s just a name for the downloaded file.
* Fill in the **URL** with ```https://ftp.mozilla.org/pub/firefox/releases/64.0.2/win64/en-US/Firefox%20Setup%2064.0.2.exe```
* Click **Add**, Click **Actions**, **Download Files**
* Click **General** from the **Sub Navigation Menu**
* Enter ==firefox.exe== in the **Command Field**
* Enter ==-ms== in the **Arguments Field**
* Click **Actions**, **Update Module**
* Assign the module to a new Policy and assign that Policy to a Group

With this Policy, anytime a computer is found without Firefox, it will automatically be deployed to that computer.








