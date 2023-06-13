## Updating Theopenem

Updates for Theopenem are handled by the Update Installer for each released update.  They can be found at [Theopenem downloads page](https://theopenem.com/downloads/).
> [!CAUTION]
> When updating Theopenem, you cannot use the full installer.  You must use the Update Installer.

> [!NOTE]
> Updates do not need applied incrementally.  For example, you can go directly from 1.5.0 to 1.5.5, skipping the releases in between.

<br />
<br />

## Update Procedure
> [!CAUTION]
> As of Theopenem 1.5.0, .NET 4.8.x is required, ensure it is installed before updating.  The previous requirement was .NET 4.6.  This only impacts the server.  The Toec requirements are still .NET 4.6

* Download the latest Update Installer
* Run the installer on every application and com server, if they are seperate
* Login to Theopenem
* You will be prompted to ***update the database***, click ***Update***

<br />
<br />

## 1.5.5 Additional Steps
> [!NOTE]
> If you are updating from 1.5.4, no other steps are required<br />
> If you are updating from any version earlier than 1.5.4, follow the steps below.

<br />

* If using the WIE, you must recreate your WIE using wie_builder v2.0.3
* If using the LIE as a USB device, you must recreate the LIE.  If you are PXE booting the LIE, no changes are needed.
* After you have logged in, select **Admin Settings->Toec->Actions->Prepare Toec Updates**.

> [!WARNING]
> Toec agents will not update until the **Prepare Toec Updates** step is performed which is helpful if you want to manually install the latest client on a few test machines before you update them all

* If you are using multiple com servers or imaging via SMB, you will need to replicate storage before Toec will update


* Your update is now complete