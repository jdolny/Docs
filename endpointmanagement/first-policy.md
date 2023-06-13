# Creating Your First Policy
This will provide you with a brief introduction on how to run some policies on your endpoints.  By this point you should have at least 1 or 2 
endpoints provisioned with Theopenem.  These can be seen from the Toems-UI from the Computers->Search Active page.  If you don’t see anything listed there yet, double 
check the Computers->Approval Request page to make sure nothing is waiting for approval.

## Create An Inventory Policy

* Select **Policies->New**
* In the **Name** field, enter **Collect Inventory**
* In the **Description** field, enter **Collect inventory once per week**.
* Change the **Frequency** to **OncePerWeek**.
* Scroll down to **Collect Inventory**, change the drop down to **Before**
* Scroll down to **Skip Server Logging Result**, **enable** it.  We don’t want a long history of inventory scans running every week clouding our logs.
* Click **Actions**, then **Add Policy**

<br />
<br />

## Create A Tracking Policy

* Select **Policies->New**
* In the **Name** field, enter **Track User Logins**
* In the **Description** field, enter **Starts the user login tracker each time the computer starts**.
* Change the **Trigger** to **Startup**
* Leave the **Frequency** at **Ongoing**
* Scroll down, **Enable Login Tracker**
* Skip the Server Logging Result once again.
* Click **Actions**, then **Add Policy**.

<br />
<br />

## Apply The Policies
In order for a Policy to take effect, it needs to be enabled and assigned to a group.

* Select **Policies->Search**
* Click **Activate** on each of the 2 policies listed
* Select **Groups->Search**
* Click **View** on the **Built-In All Computers Group**
* Click **Available Policies** from the **Sub Nav Menu**.
* **Check the box** for each of the Policies we just created.
* Click **Actions**, Add **Selected Policies**.

That completes the inventory policies.  Every computer that provisions with Theopenem will now do a weekly inventory scan as well as monitor 
 user logins.  The inventory scan will run at the next check-in for you provisioned endpoints which is every 60 minutes by default.  The tracking 
policy only runs at startup, you will need to either reboot those endpoints or restart the Toec service to test it.

<br />
<br />

## Deploy An MSI

For this example, we will create a new static group, targeting specific computers and then deploy 7-Zip.

* Select **Groups->New**
* Give the group a **name** such as **Software Deployment Test Group**
* Leave the **Group Type** as **Static**.
* Click **Actions**, **Add Group**
* Select **Add Group Members** from the **Sub Nav Menu**.
* **Check the box** next to **each computer** to add to the group.
* Click **Actions**, **Add Selected Computers**.
* Select **Modules** from the **Navigation Menu**.
* Select **Software Modules**, Then **New**
* Enter **7-Zip 22.01** for the **Name**
* Click **Actions**, **Add Module**
* Select **Upload Files** from the **Sub Nav Menu**
* **Download 7-Zip** from [this link](https://sourceforge.net/projects/sevenzip/files/7-Zip/22.01/7z2201-x64.msi/download)
* **Drop** the downloaded MSI into the **Drop Files Here box**, Click **Upload**
* Select **Policies->New** from the Navigation Menu
* Give the policy a **name** such as **Install 7-Zip**
* Change the **Frequency** to **OncePerComputer**
* Click **Actions**, **Add Policy**
* Select **Available Modules** from the **Sub Nav Menu**
* **Check the box** for **7-Zip 22.01**, Click **Actions**, **Add Selected To Policy**
* Click **Actions** then, **Activate Policy**
* Assign the Policy to the Software Deployment Test Group

The next time any of the computers in that group startup or check-in, 7-Zip will automatically be installed.

<br />
<br />

## Deploy A Software Application In Exe Format
An exe can be deployed as long as it support silent options.  This last example will silently deploy Firefox.  We’ll use a dynamic group to 
find computers that do not have firefox installed.  Finally we’ll introduce a new concept called external downloads.

* Select **Groups-> New** From the Navigation Menu
* For the **name**, enter **Computers Missing Firefox**
* Change the **Group Type** to **Dynamic**
* Click **Actions**, **Add Group**
* Select **Dynamic Criteria** from the **Sub Nav Menu**
* Change the **And/Or** dropdown to **Not**, the **Table** to **Application**, the **Field** to **name**, the **Operator** to **like**, and the **Value** to **%firefox%** ,click **Add**  
[![](https://theopenem.com/wp-content/uploads/2019/01/policy-step03.jpg)](https://theopenem.com/wp-content/uploads/2019/01/policy-step03.jpg)
* Click **Actions**, **Save Dynamic Criteria**
* Select **Modules->Command Modules->New** from the **Navigation menu**.
* For the **name** enter, **Firefox 108.0**
* Click **Actions**, **Add Module**
* Select **External Files** from the **Sub Nav menu**
* Fill in a **File Name**, such as **Firefox.exe**, it can be any name you like, it’s just a name for the downloaded file.
* Fill in the **URL** with ```https://ftp.mozilla.org/pub/firefox/releases/108.0/win64/en-US/Firefox%20Setup%20108.0.exe```
* Click **Add**, Click **Actions**, **Download Files**
* Click **General** from the **Sub Navigation Menu**
* Enter **firefox.exe** in the **Command Field**
* Enter **-ms** in the **Arguments Field**
* Click **Actions**, **Update Module**
* Assign the module to a new Policy and assign that Policy to a Group

With this Policy, anytime a computer is found without Firefox, it will automatically be deployed to that computer.








