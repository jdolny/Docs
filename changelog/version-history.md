# Version History

## 1.5.5 (6-12-23)
* Fixes a bug when imaging where the same user can only login 1 time, additional logins will cause the other imaging processes to fail

## 1.5.4 (6-2-23)
* Changes the way drivers are injected when imaging with the WIE.  They are now installed during imaging instead of needing to wait for Windows.
* Adds the ability to add Toems users to multiple groups
* Adds the ability to assign images and groups to be managed by specific users to limit access to images the user should not have access to
* Adds the option when using the WIE to not set the Windows Boot Manager as the first boot device and instead use what is currently set in the NVRAM
* Adds FFU imaging to the WIE.  This is a block image that is significantly faster than the file method, but requires using SMB imaging.
* Adds the ability to build the WIE directly from the Web UI(documentation in progress)
* Adds image replication control when using multiple com servers to control which images replicate to which server and when
* Adds the option to assign a WinPE module to a group
* Adds option to search active computers by custom attribute
* fixes an issue with toec client where policies set to run every X days may not run
* fixes computer system uptime to make it more readable 
* fixes an issue where pxe binaries would not replicate if using the newest WinPE version that no longer supports 32 bit
* Fixes an issue where categories were not sorted by name by default
* Fixes an issue where trying to sort the Toec deploy job status would throw an error
* Fixes an issue where images would still replicate to a com server that had image replication disabled
* Fixes an issue where a module file upload would hang when selection yes to replicate now if using multiple com servers
* Fixes an issue where modules cannot upload files after a postback on the page
* Fixes / Adds the ability to control the Web UI timeout from the Admin Settings->Server page
* Fixes an issue when using multiple com servers when imaging, where the wrong com server may be used
* Removes the built in help menus as the were outdated and sometimes inaccurate, will be replaced by online documentation

## 1.5.2 (12-10-22)
* Fixes an issue where the all modules list only displayed inactive modules
* Fixes an authorization error when imaging multiple computers at the same time
* Changes MFA to work with more authenticator apps
* Fixes an issue where dynamic group queries or custom computer queries returned incorrect data

## 1.5.0 (12-4-22)
* adds the ability to automatically deploy Toec to computers within your domain based on OU, security group, or custom list
* adds the ability to image a computer directly through the Toec client using WIE. Enables the ability to image without needing to pxe / usb boot.
* adds the option to not overwrite files when using a file copy module
* adds option search computers by serial number and user
* adds option to specify keyboard layout in WIE
* adds gpu collection to inventory
* adds option to use ldap security groups for predefined computer groups
* adds option to go back in on demand imaging menu if you make an incorrect selection
* adds MFA to web interface login and / or imaging login
* adds some additional fields to the group members view page
* updates ipxe to the latest version
* fixes an issue with reports when the same table is used twice with an AND condition
* fixes an issue where starting a web imaging task without password requirements will still require a login when using the WIE or using the LIE without pxe boot.
* fixes an upload issue when an active com server fails and falls back to a passive com server
* fixes an issue where WIE would fail if acquiring an ip address took to long
* fixes an issue where impersonation tasks would not run if the user was not an administrator on that computer
* pxe boot now creates a pxe file for each mac address inventoried instead of just the primary mac
* removes multicast rdv address to allow proper multicast on D class IPv4 addresses
* sets policy delete cache to enabled by default
* toec image prep no longer modifies the drivers registry path

## 1.4.8 (4-15-22)
* Software inventory now collects the uninstall string
* Adds system uptime as a computer action
* Client user logins are now collected as a user logs in instead of waiting until they log out
* Adds Linux kernel 5.17.3 - You must rebuild your client ISO to use the new kernel
* Adds option to manually create image only computers from the WebUI instead of needing to register from the client, you must know the mac address. You must rebuild your client ISO to use this new feature
* Updates the ipxe exit code, if you are PXE booting in EFI mode the boot to hd should now work
* Adds option to define the default computer page when click on computers
* Adds option to define the default page after you login
* Adds option to define the default computer sort method
* Adds the last known user column to the active computers page
* Allows periods to be used in usernames
* Adds category as criteria in asset reports
* Adds category as criteria in computer reports and dynamic groups
* Adds option to only sync a specific OU in LDAP sync
* Changes the computer service log to a more descriptive name
* Changes the default sort of group members to name instead of id
* Sets the username field on login to focus by default
* Moves the pxe boot menu editor out of com server settings and into pxe settings
* Image prep gui now automatically removes the remote access client if it was installed on the image
* Image prep gui can now install drivers onto the image for you, pulling directly from your file copy modules
* Image prep gui can now use sysprep and setupcomplete templates that are defined in Toems
* Fixes an issue where Toec could not join a computer to a domain if the object already existed in a different OU
* Fixes an issue where images with a space in the name would not upload
* Fixes some null reference logging during install
* Fixes an issue where manually collecting inventory on a group does not work
* Fixes an issue where pxe settings were not visible in mobile view
* Fixes an issue where zooming out on the web page would make the UI disappear
* Fixes an issue where ldap sync would not work if the base dn was more than 45 characters
* Fixes an issue where WinPE logins would not work on some computers - You must download the latest WIE Builder 2.0.1 and rebuild your WIE
* Fixes and issue where the WIE would not upload Windows 11

## 1.4.4 (6-5-21)
* Adds the optional ability to deploy / uploads images directly with an smb share instead of the current http method, eliminating the high cpu utilization.
* Adds new imaging workflow to make universal images easier. Such as domain joining, a first run group to run policies only after imaging, and an image prep GUI to help prepare the image for upload.
* Adds a pxe boot menu editor to the WebUI.
* Fixes an issue where the universal token would not work with PXE booting.
* Adds new debug option to the WIE to try and determine why some users are having login issues.

## 1.3.3 (3-23-21)
* Fixes an issue where an image will not upload properly if more than 1 nvram entry is found for the same hard drive
* Fixes an issue where the Toec client may stop checking in
* Adds feature where Toec.exe --prepareImage will also automatically disable hibernation

## 1.3.2 (2-15-21)
* Adds provision tasks to allow immediate group membership update on provision with both LDAP Ou's and Theopenem local groups.
* Adds a built in all computers group that always contains all computers without needing to wait for a dynamic update task or ldap sync task.
* Adds a group member count column to the group search page
* Adds option to display OU's on the group search page
* Adds enabled, protected, and on demand status columns to image search page
* Fixes issue where the Toec client would not generate properly.
* Fixes an ldap sync issue where the sync would fail if the specified base dn was not the root of the domain
* Fixes an issue where the active computer count was incorrect
* Fixes an issue where the image search page would not properly filter by category

## 1.3.1 (2-10-21)
* fixes issue where clients may not check in where region format is not English (United States)
* fixes issue where endpoints may checkin with com servers that are not endpoint management servers
* fixes issue where multicast does not use the correct storage location when using multiple com servers
* fixes issue where image uploads wouldn't work if multicast interface ip was blank
* adds option to create the LIE bootable USB both with or without secure boot support, allowing the use of newer grub binaries at the cost of not supporting secure boot.

## 1.3.0 (1-14-21)
* Remote Access / Remote Control added
* Windows Imaging Environment added
* A module can now be executed on a client without adding to a policy or group
* Client logs can now be pulled from the Toems-UI
* Toec can now be used on Windows Server
* Fixes a few multicast bugs
* Fixes a bug where Toec may crash with different regions

## 1.2.0 (12-3-20)
* CloneDeploy imaging is now a part of Theopenem
* Installation of Theopenem is now much easier

## 1.1.0 (5-19-19)
* Client push commands now work on external clients also
* Messages can be assigned to policies
* Conditions can now be applied to each module in a policy or an entire policy
* Certificates have been added to the inventory collection

## 1.0.0 (2-1-19)
* Initial Release