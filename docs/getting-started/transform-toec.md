# Transform The Toec MSI
In order for Toec to successfully communicate with Toems, it needs to trust the Toems Certificate Authority.  To do this, we need to embed your Toems Certificate 
Authority into the Toec MSI, this will be accomplished through a transform file created with Orca.  This process is only done one time, even if an update is released 
for Toec this does not need applied again.  The generated MST file will work with future versions.

###### 1. Export the Toems CA
* Login to the Toems-UI as an administrator
* Select Admin Settings->Certificates
* Click Export on the Toems CA certificate.  It will have a Type of Authority.
* Save the file when prompted, rename it to something such as Toems-CA.

---

###### 2. Modify the MSI
* Open Orca as Administrator from your Start Menu  
[![](https://theopenem.com/wp-content/uploads/2018/11/orca3.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca3.jpg)
* Select File, Open, and select either of the Toec-Agent MSI files that were included with Theopenem download package from the Server Installation.  Either 
the 32 or 64 bit MSI can be selected.
[![](https://theopenem.com/wp-content/uploads/2018/11/orca4.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca4.jpg)
* Select Transform, then New Transform  
[![](https://theopenem.com/wp-content/uploads/2018/11/orca5.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca5.jpg)
* Click on Binary under the Tables Column, Then double click on [Binary Data] next to ToemsCA.Binary.  A dialog box will open, browse to the Toems-CA certificate 
that was exported in section 1.  Ensure Read binary from filename is selected, click OK.  Click OK again when prompted to overwrite.
[![](https://theopenem.com/wp-content/uploads/2018/11/orca6.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca6.jpg)
* Keep Orca open and Log back into the Toems-UI and select Admin Settings->Client, scroll to the bottom to find Client MSI Arguments.  You should see what appears to be a long string.  It is 
actually 3 separate variables needed to install Toec.  Keep this window open and return to Orca.
* In Orca, select Property under the Tables column.  In the right side, right click on the empty white space and select Add Row.  
[![](https://theopenem.com/wp-content/uploads/2018/11/orca8.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca8.jpg)
* For the property, enter **SERVER_KEY** case sensitive, and for the value copy the value from the Toems-UI SERVER_KEY=
* Click OK  
[![](https://theopenem.com/wp-content/uploads/2018/11/orca9.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca9.jpg)
* Repeat the previous step for the **CA_THUMBPRINT** and **COM_SERVERS** properties.  Your Orca window should now look something like this, but with your values.
[![](https://theopenem.com/wp-content/uploads/2018/11/orca10.jpg)](https://theopenem.com/wp-content/uploads/2018/11/orca10.jpg)
* From the top menu bar Select Transform, then Generate Transform, for the filename use something such as Toec-Transform.
* Close Orca

!!! success "This Concludes Transform The Toec MSI. Check this off of your Installation checklist now."


