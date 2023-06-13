## Imaging Boot Method

By this point in the guide, you should have selected an imaging environment.  Before you can begin imaging you must decide how you will boot into the imaging environment.  Each image environment
provides the option of booting from CD-ROM, USB Device, or a PXE boot via your network.  The WIE can also be booted directly from a Toec WinPE Module.  
<br />
<br />

## CD-ROM / ISO Boot
You should have downloaded an ISO for either the WIE or LIE, or possibly both.  You can simply burn the ISO to a cd using your favorite program. (Yes, I know that nobody still uses a CD-ROM)
<br />
<br />

## USB Boot
You should have downloaded an ISO for either the WIE or LIE, or possibly both.  You can utilize Rufus to copy the ISO to a USB device.<br/>
**To Use Rufus**
* Download the latest version from https://rufus.ie/en/ and run it
* Insert your USB Device and select it from the Device list<br/><br/>
![ rufus-1.png ]( /images/rufus-1.png )
* For the boot selection, click on the **SELECT** button, then browse to your LIE ISO or WIE ISO.<br/><br/>
![ rufus-2.png ]( /images/rufus-2.png )
* If you will be booting legacy BIOS computers, change the **Partition Scheme** to **MBR** and the **Target System** to **BIOS OR UEFI**, otherwise leave this setting as is. <br/><br/>
![ rufus-3.png ]( /images/rufus-3.png )
* Leave all other options to their defaults and click on **START**<br/><br/>
![ rufus-4.png ]( /images/rufus-4.png )
<br />
<br />

## PXE Boot
A TFTP server was already installed and configured to work with Theopenem. You just need to tell your computers to PXE boot from it. This requires a small change to your DHCP Server.

**If Using A Windows DHCP Server**
* Set your DHCP Scope **Option 66** to **Your Theopenem Server Ip**
* Set your DHCP Scope **Option 67** to **pxeboot.0** (That is a zero) 

**If Using Any Other DHCP Server**
* Consult it's documentation to Set the boot server to your Theopenem Server IP and the boot file to pxeboot.0 ( That is a zero )

<br />
<br />

## Toec WinPE Module
The final method to boot involves using Toec to boot to the WIE.  As the name implies, this method is only valid for the WIE and with computers that are being managed by the Toec client.  The computer must be booted into Windows with the Toec service running.
It should also be noted, that you can only deploy
images via Toec WinPE.  You cannot upload them with this method.
### Create A WinPE Module
1. Select Modules->WinPE Modules
2. Select New
3. Provide a Display Name and optionally a description
4. Select **Actions** then **Add Module**
5. Select **Upload Files**

> [!NOTE]
> There are 2 files that need uploaded for the WinPE module.  These files currently must not be renamed, a future version will allow for renaming these files.
* boot.sdi
* WinPE10x64.wim

> [!NOTE]
> If you created the WIE from the Toems WEB UI, you can find the files at **C:\Program Files\Theopenem\tftpboot\boot** <br/>
> If you created the WIE from the stand alone WIE Builder 2.0.3 utility, you can find the files in the **Builds\tftpboot\boot folder** of the **wie_builder**

6. Drop the 2 files into the Upload box and click **Upload**

### Assign The WinPE Module To A Computer / Group
1. Select Computers
2. Select View on the computer you want to deploy
3. Select **Image Settings**
4. Select the image to deploy from the Image dropdown list
5. Select the WinPE Module you created earlier in the WinPE Module dropdown list
6. Select **Actions** then **Update Computer**
7. Finally, select **Actions** then **Deploy Image Via Toec**

The computer will automatically reboot and begin imaging without the need for any human interaction at the computer.