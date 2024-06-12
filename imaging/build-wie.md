## Build the Windows Imaging Environment

The WinPE imaging environment is not distributed with Theopenem due to licensing reasons. You will need to build it yourself. 
Theopenem provides 2 options to build the environment:
<br />
<br />

## Option 1: Build From the Web UI
As of Theopenem 1.5.4, the WIE can be built directly from the Toems UI.  It requires some setup work but will make things easier in the future if you take the time to complete it.

1. On your Theopenem server, begin by installing the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit).  On that page click the link that says **Download the Windows ADK for Windows 11, version xxxx**

2. During installation, select all default options until you reach the **Features Page**.  On the features page select ***Deployment Tools***, uncheck everything else.<br />
![ wie-build-1.png ]( /images/wie-build-1.png )

> [!NOTE]
> Theopenem expects to find the Windows Kit in the default location (like "C:\Program Files\Windows Kits").
> If you installed it on another drive (like E:\Windows Kits) you can try to use a "junction" (link) in the filesystem.<br />
> Open CMD as Administrator and run:  <br />
> mklink /J "%Programfiles%\Windows Kits" "E:\Windows Kits"  <br />
> (change last path to the path where you installed the Windows Kit)

3. Once again navigate to the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit).  This time click the link that says **Download the Windows PE add-on for the Windows ADK, version xxxx**

4. Install the Windows PE add-on will all the default options

> [!NOTE]
> The next few steps will create a local administrator on your Toems Server.  This user is required to build the WIE as the Application Pool in IIS that Theopenem runs under, does not have enough permissions to mount a wim.
> If you are not comfortable with this, proceed to using the Standalone tool to build the environment

5. Open the Local Users and Groups Manager from the Windows Run command **lusrmgr.msc**<br />
![ wie-build-2.png ]( /images/wie-build-2.png )

6. Right click on **Users** and select **New User**

7. Fill in a username(something like **wie_builder_admin** is nice and descriptive).

8. Create a password for the user, you will need to enter this password in the Toems WebUI also, don't forget it.

9. Uncheck User must change password at next login

10. Check User cannot change password

11. Check Password never expires

12. Click **Create**, Then **Close**<br />
![ wie-build-3.png ]( /images/wie-build-3.png )

13. Find your newly created user in the list, right click and select properties<br />
![ wie-build-4.png ]( /images/wie-build-4.png )

14. Click the **Member Of** tab

15. Click **Add**

16. Type **administrators** in the box and select **OK**

17. Click **OK** and close the Local Users and Groups Management tool

18. Login to the Toems UI

19. Select **Admin Settings->Impersonation Accounts**

20. Create a new account providing the username and password you created back in steps 7-8.

21. Select **Admin Settings->PXE / Boot Menu->WIE Generator**

22. Change the Run As drop down to the impersonation account you created in step 20

23. Change the Time Zone / Input Locale: / Language if needed

24. Place a checkbox in the com server that thiis environment will communicate with by default

25. Select **Actions** then **Generate WIE**

26. The Active Build Processes should populate while the environment is building.  This process may take up to 10 minutes to complete.  You can navigate away from this page while it is running.

27. The Build Date will populate once the build has completed

28. Select **Actions** then **Download ISO** to download the environment.

> [!WARNING]
> If you plan on PXE booting this environment.  You will need to copy the tftpboot folder located at <br/>
**C:\Program Files\Theopenem\Toems-API\private\wie_builder\Builds\tftpboot** <br/>
and merge it with Theopenem Tftp folder located at <br/>
**c:\program files\theopenem\tftpboot**  <br/>
You must copy the tftpboot folder to every com server that will provide PXE support. <br />
Finally, Change your PXE Mode in **Admin Settings->PXE / Boot Menu->PXE Settings** to the appropriate WinPE architecture. WinPE also works with the Toems Proxy DHCP to support both Legacy BIOS and EFI PXE booting simultaneously. 

<br />
<br />

## Option 2: Build From A Standalone tool
Use this option if you are having problems with building the environment from the UI, or would rather use the standalone tool to build it on any computer.
1. On your Theopenem server, begin by installing the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit).  On that page click the link that says **Download the Windows ADK for Windows 11, version xxxx**

2. During installation, select all default options until you reach the **Features Page**.  On the features page select ***Deployment Tools***, uncheck everything else.<br />
![ wie-build-1.png ]( /images/wie-build-1.png )

3. Once again navigate to the [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit).  This time click the link that says **Download the Windows PE add-on for the Windows ADK, version xxxx**

4. Install the Windows PE add-on will all the default options

5. Download and extract the **WIE Builder 2.0.3** from [Theopenem downloads](https://theopenem.com/downloads)

6. Login to the Toems-UI and select **Admin Settings->Client Com Servers**.  Copy the URL for the com server this WIE will connect to.

7. In the package that was unzipped, **right click** on **Manual-ToemsPE-Build.cmd** and select **edit**

8. Paste in the com server URL where it says **ComServerURL=**.  Overwriting the http://0.0.0.0/ with your com server url.

9. Save and close the file.

10. Right click on **Manual-ToemsPE-Build.cmd** and select **Run as Administrator**

11. After the the script is done(It may take up to 10 minutes), look in the builds directory for the output.

12. If you are PXE booting, merge the tftp folder with your Theopenem Tftp Folder located at **c:\program files\theopenem\tftpboot**.  You must do this on every com server. Change your PXE Mode in **Admin Settings->PXE / Boot Menu->PXE Settings** 
to the appropriate WinPE architecture. WinPE also works with the Toems Proxy DHCP to support both Legacy BIOS and EFI PXE booting simultaneously. 


