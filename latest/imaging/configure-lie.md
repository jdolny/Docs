## Configure The LIE
The Linux imaging environment is already included with Theopenem and very easy to configure.  If you plan on PXE Booting with the LIE, there is nothing additional to configure,
you can skip this step.  These directions are only if you need to boot the LIE with a USB / ISO.
<br/>
<br/>

1. Login To Theopenem WebUI
2. Navigate to **Admin Settings->PXE / Boot Menu->LIE Generator**
3. Leave all options to their defaults except for Secure Boot Support.  It is recommended to disable Secure Boot Support as it no longer works reliably on newer hardware.
4. Select **Actions** then **Generate ISO**
5. After a few minutes a dialog box will open where you can save the ISO.