# Building the Windows Imaging Environment

Unlike the Linux Imaging Environment, the WinPE imaging environment is not distributed with Theopenem due to licensing reasons. You will need to build it yourself. 
I have created an automated tool to do this for you. The WinPE Imaging Environment must be created on a Windows 10 computer. Only WinPE 10 and newer will be supported, 
however the WinPE Imaging Environment supports imaging client computers with Win7, Win8, or Win10.

* Begin by installing the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit){:target="_blank"}.  On that page click the link that says **Download the Windows ADK for Windows 10, version xxxx**

* During installation, select all default options until you reach the **Features Page**.  On the features page select Deployment Tools, uncheck everything else.
[![](https://theopenem.com/wp-content/uploads/2021/01/2.png)](https://theopenem.com/wp-content/uploads/2021/01/2.png)

* Once again navigate to the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit){:target="_blank"}.  This time click the link that says **Download the Windows PE add-on for the ADK, version xxxx**

* Install the Windows PE add-on will all the default options

* Download and extract the **WIE Builder** from [Theopenem downloads](https://theopenem.com/downloads){:target="_blank"}

* Login to the Toems-UI and select **Admin Settings->Client Com Servers**.  Copy the URL for the com server this WIE will connect to.

!!! info "The WIE does not have the ability to dynamically select a com server like the LIE does.  It will only connect to the server that's been copied from the previous step"

* In the package that was unzipped, **right click** on **ToemsPE-Build.cmd** and select **edit**

* Paste in the com server URL where it says **ComServerURL=**.  Overwriting the http://0.0.0.0/ with your com server url.

* Save and close the file.

* Right click on **ToemsPE-Build.cmd** and select **Run as Administrator**

* After the the script is done(It may take up to 10 minutes), look in the builds directory for the output.

* If you are PXE booting, merge the tftp folder with your Theopenem Tftp Folder located at **c:\program files\theopenem\tftpboot**.  You must do this on every com server. Change your PXE Mode in **Admin Settings->PXE / Boot Menu->PXE Settings** 
to the appropriate WinPE architecture. WinPE also works with the Toems Proxy DHCP to support both Legacy BIOS and EFI PXE booting simultaneously. 

* If you are using a USB / ISO, there are 3 iso files. A 32 and 64 bit ISO, that both work on Legacy BIOS and EFI systems, and a Super ISO. The Super ISO works on all 32 and 64 bit Legacy BIOS, and EFI systems with a single ISO. 
You can use something like Rufus to copy these ISO’s to USB.

