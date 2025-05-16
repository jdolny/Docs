# Images
Images are used for deploying an OS to various endpoints.  The following pages allow you to manage those images.

## Search
The search page displays the list of current images. Filtering options include: <br/>

* Search by image name
* By category
* By limit

#### Actions
Action | Description
------|------------
Delete Selected Images | Permanently deletes the selected images.  Any images that are protected will not be deleted.

<br />
<br />

## New
The new image page is used for creating a placeholder for an image before it is uploaded.  This can be useful if you need to set specific options for the image before it is uploaded.  Most people probably just use the 
On Demand upload from the imaging client to create the image, but it's good to know that this other option exists.

Field | Description
------|------------
Image Name | The name of the image.  Characters can only be alpha numeric and dash and underscore.
Imaging Client Environment | The environment that will used to deploy / upload the image.   Either WinPE (recommended) or Linux.  This has nothing to do with the OS that you are imaging.
Image Type | Specifies if the image will be captured at the Block or File level.  It is currently recommened to use Block for the LIE and File for the WIE.  Block support has been added for the WIE but is not yet as stable as File.  If the environment is set to WinPE, there is a 3rd option for both.  This will upload both a block image and a file image and use the best option when deploying.
Image Description | A place for an optional description of the image.
Protected | A protected image cannot be deleted via the web ui or uploaded. Helpful to avoid accidentally overwriting an image if someone accidently selects upload instead of deploy. After an image has uploaded, this setting automatically enables itself.
Available On Demand | Specifies if the image can be used directly from the Client Imaging OS menu, instead of a web based task.

#### Actions
Action | Description
------|------------
Add Image | Creates the image placeholder.

<br />
<br />

> [!NOTE]
> The following additional pages are available after an image is added or when selecting the view button on a specific image from the search page.

## General
The general page can be used to update some general information about the image.  Note that the Imaging Client Environment and Image Type cannot be modified once set.

Field | Description
------|------------
Image Name | The name of the image.  Characters can only be alpha numeric and dash and underscore.
Imaging Client Environment | The environment that will used to deploy / upload the image.   Either WinPE (recommended) or Linux.  This has nothing to do with the OS that you are imaging.
Image Type | Specifies if the image will be captured at the Block or File level.  It is currently recommened to use Block for the LIE and File for the WIE.  Block support has been added for the WIE but is not yet as stable as File.  If the environment is set to WinPE, there is a 3rd option for both.  This will upload both a block image and a file image and use the best option when deploying.
Image Description | A place for an optional description of the image.
Protected | A protected image cannot be deleted via the web ui or uploaded. Helpful to avoid accidentally overwriting an image if someone accidently selects upload instead of deploy. After an image has uploaded, this setting automatically enables itself.
Available On Demand | Specifies if the image can be used directly from the Client Imaging OS menu, instead of a web based task.
Enabled | Only enabled images can be deployed. If you want to keep an image around but not let anyone deploy it, then disable it.

#### Actions
Action | Description
------|------------
Update Image | Updates the image options.
Delete Image | Permanently deletes the selected image.

<br />
<br />

## Image profiles
Image profiles are used to control various options for how the image deploys and uploads.  It is also fundamental for using a Universal image to control how different hardware is handled.


## Image Profiles->Search Profiles
The list of available images profile for the current image. Images can have multiple profiles to support multiple configurations. A default profile is always generated when an image is created. 
Profile options will appear different depending on the Imaging Environment assigned to the image.

## Image Profiles->New Profile
Create a new blank profile.  This should rarely be used.  Instead create a clone of the default profile that was created with the image.

> [!NOTE]
> The following additional image profile pages are available when the view button is selected on a specific image profile from the search page.

## Image Profiles->General
This page is used to update the general properties of the Image profile.

Field | Description
------|------------
Profile Name | The name of the image profile
Profile Description | An optional description of the profile
Model Match | Model match is used to automatically deploy an image to any machines that match the model defined here. This setting should be used with caution as it is very easy to image a machine even without starting any tasks. You must also be careful to not overwite a computer that you want to upload an image from. To use this setting enter the model name in this field. The model string can be found in the upload and deploy logs.
Model Match Criteria | Specifies how the Model Match should be evaluated, such as a partial match or an exact match.

## Image Profiles->PXE Boot Options
Specifies the kernel and boot image that are used when pxe booting computers that have this image profile assigned and an active task has been created. This is only used when an active web task ( deploy or upload) for the computer with this profile is created. It does not apply to on demand or any other mode. Kernel arguments can also be passed in from here. This only applies to the Linux imaging environment and only if pxe booted.

## Image Profiles->Task Options
Field | Description
------|------------
Enable Web Cancel | If a web task is cancelled from the web interface, the task will disappear, but will continue to run on the client itself. Checking this box will stop the task on the client and perform the task completed action. This would mainly be used for debugging. Sometimes an image process will appear to have frozen. If web cancel is enabled it should stop the client and upload any part of the log it currently has. This must be enabled before a task is started to work.
Task Completed Action | Specifies what should happen when a client task finishes or errors out.

## Image Profiles->Upload Options
Set various options for how the image is uploaded

Field | Description
------|------------
Remove GPT Structures (LIE) | A hard drive can have an mbr and a gpt partition table. Hard drives that have both will not function with Theopenem. If you are certain that you are using mbr, this will clear out the gpt part of the table before the upload.
Don't Shrink Volumes (LIE) | By default, when a Block image is uploaded, all ntfs or extfs filesystems that are larger than 5GB are shrunk to the smallest volume size possible to allow restoring to hard drives that are smaller than the current one being captured. If this is causing problems you can disable that here.
Don't Shrink LVM Volumes (LIE) | Same as above but specifically for LVM. Don’t Shrink Volumes will supersede this setting, but not vice versa.
Skip Hibernation Check (LIE) | Before an image is uploaded, it checks for the presence of hiberfil.sys and cancels the upload if it exists. Uploading an image while hibernated can completely break the original image. Enabling this option will skip this check.
Skip Bitlocker Check (LIE) | Bitlocker is not supported and must be disabled before uploading an image. CloneDeploy will attempt to see if Bitlocker is enabled and error out if so. Enabling this option skips the bitlocker check.
Compression Algorithm (LIE) | A few different ways to compress or not compress your image, lz4 is the fastest
Compression Level (LIE) | Higher number is greater compression
Only Upload Schema (LIE + WIE) | If you want to control what hard drives or partitions to upload, this is the first step. Turn this setting On and start an upload task. Instead of uploading an entire image, it will only upload the schema.
Use Custom Upload Schema (LIE + WIE) | If you want to control what hard drives or partitions to upload, this is the second step. Check this box and a new table will be available to visually pick your partitions but only after you have uploaded the schema. The table will list each hard drive and partition that was found, simply check or uncheck the one’s you want. There is also an option for each partition called fixed. If this box is checked the filesystem for that partition will not be shrunk. This is a more flexible option than setting the Don’t shrink volumes setting which applies to all partitions. The Upload schema only box must be unchecked when use custom upload schema is checked. This does not modify the schema that was uploaded, it generates a new one that is stored in the database, the original is never modified.

## Image Profiles->Deploy Options
Set various options for how the image is deployed

Field | Description
------|------------
Change Computer Name (LIE + WIE) | When this option is checked the computer’s name will be updated to match what you have stored in Theopenem either by modifying the sysprep file or the registry during the imaging process.
Set Bootmgr As First Boot Device (WIE) | Sets the Windows boot manager to the first boot device on EFI systems, otherwise leave boot order as is when imaging occurred.
Don't Expand Volumes (LIE) | During the deployment process ntfs, extfs, and xfs filesystems are expanded to fill the full partition. Setting this option will disable that.
Update BCD (LIE) | If your computer does not boot after deployment, try turning this on. Theopenem will update the BCD boot file on Windows machines to correct the boot problem.
Randomize GUIDs (LIE) | Generates new partition Guids on GPT tables to avoid collisions.
Fix Boot Sector (LIE) | This fixes the partition that is set to active / boot in cases where the NTFS geometry is incorrect. This should almost be left checked. Only applies to mbr partition tables.
Don't Update NVRAM (LIE) | When deploying an EFI image. The NVRAM is updated in order to make the machine bootable. In some cases this may cause problems and can be disabled here. Many new systems will automatically detect the correct partition to boot even without correct NVRAM values.
Create Partitions Method (LIE + WIE) | This option selects how the partition tables will be setup on the client machine before image deployment. The default option is Dynamic and should work for most situations. This means that Theopenem will generate the appropriate sized partitions based on many different factors. It could possibly shrink or grow a partition to make them fit the new hard drive.

* Use Original MBR / GPT - Restores the exact same partition table that was used on the original image. This option should only be used if you are having problems with the dynamic option. You can also only use this if the new hard drive is the same size or larger than the original. If you create an image from 80GB hard drive and you deploy to a 120GB hard drive, the 120GB hard drive will effectively become an 80GB hard drive. You would manually need to resize the partitions.
* Dynamic - Generates / resizes the appropriate partitions to fit on the destination drive based on many different factors.
* Standard - A simple standard partition table is created, as if a new installation with default partitioning and then only the OS volume image is restored. Using this option enables you to deploy an EFI image to a legacy bios machine, and vice versa. When using this option you must select on a single partition to deploy in the modify image schema.
* Custom Script - Allows you to make your own partitions via a shell script. You can use the partitioning tools available in the client boot image. These include fdisk, gdisk, and parted.

 | 
------|------------
Force Dynamic Partition For Exact Hdd Match (LIE) | When deploying an image to a hard drive that is the exact same size as the source. They dynamic partition method is not used even if selected. The Use Original MBR / GPT option is used. This option will disable that and force the Dynamic partition option to be used, for cases where the mbr / gpt does not restore properly.
Modify The Image Schema (LIE + WIE) | Checking this box gives you control over what hard drives and partitions will be deployed, where they will restore to and give you custom sizing options. A new table will be displayed with these options. Any hard drive or partition that is checked will be deployed. Hard drives are always deployed in the order they are listed in this table. You can modify this by setting a value in the Destination box. For example, if the first hard drive listed in the table was originally /dev/sda it will be restored to the first hard drive that is found during the imaging process, it may also be /dev/sda or may not be. If you wanted to send this hard drive to the second hard drive in the system, you would set the Destination to /dev/sdb or whatever the matching hard drive name may be. Next, each partition can be set with a Custom Size. Enter a size you want the partition to be and select a unit for the size. Current options are MB, GB, and %. If you are using a percentage they do not need to add up to 100. Whatever percentage is remaining will automatically be spread across the remaining partitions. The same is true when using MB or GB. Finally each partition has check box called Fixed. When this box is checked the partition will not be adjusted to fit the new hard drive size. It will remain the exact same as the original partition that you uploaded. Partitions smaller than 5GB use this logic automatically. When you change the deploy schema, the original schema is never modified, a new copy is created and stored in the database so don’t worry about messing anything up. There is also an option to export the schema you have defined, I may ask for this for debugging info if you are having problems. One final note, if you set a custom size to use a percentage, the minimum client size that is displayed in the profile list will show N/A. This is because a minimum size cannot be known without knowing the size of the hard you are deploying to.

## Image Profiles->Multicast Options
Used to set custom multicast arguments for the image.  Argument list can be found at http://www.udpcast.linux.lu/cmd.html

## Image Profiles->Scripts
This view allows you to set any custom scripts you want to run during the imaging process. They are only applied to deploy or multicast tasks. 
To create the script select **Modules->Script Modules** and create the script with a script type of ImagingClient. The priority can be used to control the order if multiple scripts are assigned. Lower numbers run first. You can also select when to run the script in the imaging process. 
* Before Imaging occurs - this happens at the beginning of the processing of each hard drive while no partitions are currently mounted.    
* Before File Copy - this happens at each partition while it is still mounted and before any file copy modules have run.
* After File Copy - this happens at the end of each hard drive processing while no partitions are mounted and after any file copy modules have run.

## Image Profiles->Sysprep
This view allows you to set any sysprep modifications you want to run during the imaging process. They are only applied to deploy or multicast tasks. To create the sysprep mod select **Modules->Sysprep Modules**. The priority can be used to control the order if multiple syspreps are assigned. Lower numbers run first.

## Image Profiles->File Copy
Allows you to copy additional files or folders to a specific partition after the image is applied. They are only applied to deploy or multicast tasks. Like scripts and sysprep they can be assigned a priority to run. Lower numbers run first. The Destination Partition is just the number of the partition you want to send to. You can find the correct number by viewing the image schema. If you are copying to an LVM partition you would use volumegroupname-logicalvolumename for the destination.


## Replication
If you are using multiple com servers, the image needs to replicate to each com server.  This page shows the status of that replication and the following option:

Field | Description
------|------------
Image Replication Mode | Sets how the replication is handled for this image

* Global Default | Uses the global replication mode defined in **Admin Settings->Server**
* All | This image will replicate to all other com servers
* None | The image won't replicate to any com servers, it will only exist on the server it was uploaded to, or the SMB share if using SMB imaging.
* Selective | The image will replicate to any of the selected com servers.

#### Actions
Action | Description
------|------------
Update Image | Updates the image options.
Delete Image | Permanently deletes the selected image.

<br />
<br />

## Categories
Categories operate like tags and allow you to organize your modules and filter by them on the search page. Categories can be defined in **Global Properties->Categories**

#### Actions
Action | Description
------|------------
Update Image | Updates the image options.
Delete Image | Permanently deletes the selected image.

<br />
<br />

## Image Schema
Displays the Schema for the image. When deploying an image, all of the partitioning decisions are based off the information found in this file. This view is only for informational purposed, nothing can be changed here. 
The physical file is located in the root of the image folder and should never be changed.

#### Actions
Action | Description
------|------------
Delete Image | Permanently deletes the selected image.

<br />
<br />

## Image History
Displays a list of events that happened involving this image.

#### Actions
Action | Description
------|------------
Delete Image | Permanently deletes the selected image.

<br />
<br />

