## Imaging Environments

Imaging Environments are specialized OS’s that are used to boot client computers in order to upload images from or deploy images to.  You must decide which environment best fits your needs.
Many of Theopenem users will ultimately end up using both environments for various reasons.  There is no problem with that, just be aware that images that are created in one environment 
are not interchangeable with the other environment. There are 2 environments to choose from, each having their pros and cons.
<br />
<br />

## Windows Imaging Environment (WIE)
This is the recommended way to image Windows.  It provides the greatest hardware compatibilty as well as support for Secure Boot. It also provides support for booting Dell in Raid mode. However, it's 
large size(500MB) can take a few extra minutes to load, if PXE booting, vs the LIE.  This environment cannot be distributed with Theopenem due to licensing restrictions, but Theopenem provides an
automated tool to create the environment.  The WIE has the ability to PXE boot, but has some drawbacks when compared to the LIE.
If PXE booting the WIE, there is no option to only boot into the environment if an imaging task is waiting.  This means you cannot set your NIC as the first boot device when using the WIE.  You must
manually select your NIC from your bios boot menu each time you want to image.  This is typically as simple as pressing F11 during boot and selecting your NIC. 
<br />
<br />

## Linux Imaging Environement (LIE)
The faster and more versatile of the 2 imaging environments.  This environment can image nearly any Windows or Linux computer.  It is faster than the WIE for both imaging and PXE booting, 
but has some cons.  It does not support secure boot or Dell computers with the hard drive set to RAID.  You will need to disable secure boot and change your hard drive mode to AHCI to use this
environment.  If you are looking for the fastest possible imaging, this is the environment to choose.  As long as disabling secure boot doesn't bother you.  Also, this environment is already included with 
Theopenem and ready to use.  No additional building is required.  The LIE offers a better PXE boot experience when compared to the WIE.  If you would like to leave your NIC as your first boot device so the
computer can be imaged without physically being there, the LIE can offer that.  It will only boot into the imaging environment if an imaging task is waiting for that computer.  Otherwise, it will boot to your OS.
It should be noted, that setting your NIC as your first boot device is not recommend as it could be considered a security issue.
<br />
<br />

## WIE vs LIE
Item  | WIE | LIE
------|-----|-----
Supported Filesystems | Fat32 / NTFS | FAT(12-16-32) / NTFS / exFAT / ext(2-3-4) / XFS
Image Capture Mode | File / Block | File / Block
Supported Partition Type | MBR / GPT | MBR / GPT
Supported Bios Type | Legacy / EFI | LEGACY / EFI
Supported Boot Methods | ISO / USB / PXE | ISO / USB / PXE
Secure Boot Support | Yes | No
Speed Comparison | Slower PXE Boot, Slower Imaging | Faster PXE Boot, Faster Imaging
Multicast | Yes - Only with file based image | Yes - Both file and block based image supported
Extended Partitions | No | Yes
LMV Support | No | Yes
Dell RAID Support | Yes | No
Supports Dual Boot | No | Yes - Results may vary
Use single image for both legacy bios and EFI | Yes | Yes
Restore Image To Smaller Hard Drive | Yes - File based image only | Yes - NTFS and ext(2-3-4) only, block and file based
Expand Image To Fill Larger Hard Drive | Yes | Yes - NTFS, XFS and ext(2-3-4) only
Change Computer Name During Imaging | Yes | Yes - NTFS only
Driver Injection During Imaging  | Yes | Partial - Drivers are copied during imaging and installed after Windows boots