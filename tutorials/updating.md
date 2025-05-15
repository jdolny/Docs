## Updating Theopenem

Updates for Theopenem are handled by the Update Installer for each released update.  They can be found at [Theopenem downloads page](https://theopenem.com/downloads/).
> [!CAUTION]
> When updating Theopenem, you cannot use the full installer.  You must use the Update Installer.

> [!NOTE]
> Updates do not need applied incrementally.  For example, you can go directly from 1.5.0 to 1.5.7, skipping the releases in between.

<br />
<br />

## Update Procedure

* Download the latest Update Installer
* Run the installer on every application and com server, if they are seperate
* Login to Theopenem
* You will be prompted to ***update the database***, click ***Update***

<br />
<br />



## 1.5.7 Additional Steps
### If updating from 1.5.6:
* If you are managing endpoints with Toec, you must prepare Toec updates.  **Admin Settings->Toec->Actions->Prepare Toec Updates**.
* If you are using multiple com servers you must also replicate the storage **Admin Settings->Task Scheduler->Storage Sync->Run Now**


### If updating from any version prior to 1.5.6
* If using the LIE as a USB device, you must recreate your LIE USB device.  If you are PXE booting the LIE, you must recreate your default boot menus.  **Admin Settings->PXE Boot Menu->Global Boot Menu->Actions->Create Boot Files**
* If you are managing endpoints with Toec, you must prepare Toec updates.  **Admin Settings->Toec->Actions->Prepare Toec Updates**.
* To use the new Winget feature, you must either reboot the server or restart the World Wide Web Publishing service.  Then run a Winget sync. **Admin Settings->Task Scheduler->WinGet Manifest Importer->Run Now**.  It should take about 10 minutes before the Winget module packages are populated.


* If you are using multiple com servers or imaging via SMB, you will need to replicate storage before Toec will update


> [!WARNING]
> Toec agents will not update until the **Prepare Toec Updates** step is performed which is helpful if you want to manually install the latest client on a few test machines before you update them all
* Your update is now complete