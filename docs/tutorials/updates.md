# Updates

Updates for Theopenem are handled by the Update Installer for each released update.  They can be found at [Theopenem downloads page](https://theopenem.com/downloads/).

!!! danger "When updating Theopenem, you cannot use the full installer.  You must use the Update Installer. "

!!! info "Updates are not incremental.  For example, you can go directly from 1.2.0 to 1.3.0, skipping 1.2.1"

###### Update Steps
* Download the latest Update Installer
* Run the installer on every application and com server, if they are seperate
* Login to Theopenem
* You will be prompted to update the database, click Update
* After you have logged in, select **Admin Settings->Toec->Actions->Prepare Toec Updates**.  Toec agents will not update until this step is performed which is helpful if you want to manually install the latest client
on a few test machines before you update them all
* If you are using multiple com servers, you will need to replicate storage before Toec will update
* See below for specific updates steps required for your version
* Your update is now complete

## 1.5.0 Update Additional Steps
* Install .NET 4.8 (Previous versions required .NET 4.6.  The requirement is now .NET 4.8.  It can be [downloaded here](https://dotnet.microsoft.com/download/thank-you/net48).  .NET 4.8.1 is also compatible.  .NET 5.0 and greater are not compatible.  They are fine if they are installed, 
but they will not serve as a substitute for .NET 4.8.x.
* If using the WIE, you must recreate your WIE using wie_builder v2.0.2
* If using the LIE as USB a device, you must recreate the LIE.  If you are PXE booting the LIE, no changes are needed.


## 1.5.2 Update Additional Steps
* If you are updating from a version prior to 1.5.0, follow the steps for a 1.5.0 upgrade above
* If you are updating from 1.5.0, no additional steps are required.
