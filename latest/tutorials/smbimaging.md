# Using SMB Imaging
Be default, Theopenem deploys images via Http and uploads images via udpcast ports 9000-10000.  This has a few benefits:<br/>

* No need for an SMB share
* The ability to deploy an image anywhere in the world.
* Multiple com servers can be used to split the imaging load

<br />

There are times when you might want to deploy / upload your images directly to an SMB server:<br/>

* Imaging may not work properly for some models over Http
* Imaging is faster over smb
* You want to use the FFU imaging format, which requires SMB
* Significantly less CPU usage during imaging

The downside to using SMB imaging, is that each computer must be able to directly access the SMB share.  This typically isn't a problem if you are imaging from a central location anyway.  This will limit your imaging abilities to only work within your network.

<br />
<br />

> [!NOTE]
> If you are already using multiple com servers, which requires an SMB share, then you can skip to Step 3 **Enable SMB Imaging** of this guide, otherwise continue along to configure an SMB share.


## 1. Setup the SMB Share
<br />
The easiest way to setup a share is to use your existing toems local storage directory and that's what this guide will focus on.  If you want to setup a share on different file server that is fine also, just be sure your computers can reach that server.
<br/>
<br/>

1. Create a user that will be used to connect to the share.  It can be a local user on Theopenem server or a domain account.  This guide is using a local user named **toems_smb_user**
2. In **Windows Explorer** navigate to c:\ and locate **c:\toems_local_storage** (unless you changed the default location during intall)
3. Right click on the folder and select properties<br />
![](/latest/images/smbimaging-1.png)<br /><br />
4. Select the **Sharing** tab then **Advanced Sharing**<br />
![](/latest/images/smbimaging-2.png)<br /><br />
5. Check the **Share this folder** box and give it a name such as **toems_smb**
6. Select **Permissions**<br />
![](/latest/images/smbimaging-3.png)<br /><br />
7. Remove the **Everyone** user and add your user from step 1 with Full Control<br />
![](/latest/images/smbimaging-4.png)<br /><br />
8. Select OK
9. Select the **Security Tab** and select **Edit**
10. Add your user from step 1 with **Modify Permissions**<br /><br />
![](/latest/images/smbimaging-5.png)<br />
11. Click Ok then Close

<br />
<br />


## 2. Enable SMB Storage Location
1. Login to the **Toems-UI**
2. Select **Admin Settings->Storage Location**
3. Change the **Storage Type** to **SMB**
4. Change the **Storage Path** to the UNC path of the share using either the FQDN or IP Address, <br/>such as ```\\TOEMS-VM-01.theopenem.com\toems_smb``` or ```\\192.168.56.1\toems_smb```
5. Enter the username for the user that will connect to the share (do not include the domain)
6. Enter the password for the user that will connect to the share
7. If the user is a domain user, enter the **Domain** in FQDN format
8. Select **Actions** then **Update Storage Settings**
9. Select **Dashboard** from the navigation menu.  You should now see a Remote Storage listed.  If it is not listed, something is not configured correctly.

> [!TIP]
> If you setup an smb share that was not at the same location as the toems local storage, you need to replicate everything to the share.  This can be done by navigating to **Admin Settings->Task Scheduler** and clicking **Run Now** on **Storage Sync**

<br />
<br />


## 3. Enable SMB Imaging
1. Login to the **Toems-UI**
2. Select **Admin Settings->Imaging Client**
3. Enable **Upload / Deploy Direct to SMB**
4. Select **Actions** then **Update Server Settings**

You are now ready to upload and deploy images just as did before except now the transfer will happen over SMB instead of Http.