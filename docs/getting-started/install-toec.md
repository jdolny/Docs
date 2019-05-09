# Install Toec Via Cmd Or Powershell
Now that the Toec MSI has been transformed, we can begin installing it to some test clients.  The Toec MSI can only be installed from a cmd line or other deployment tool.  There 
is no GUI and cannot be installed just double clicking the file.  This section will cover installing Toec from cmd or powershell.  In the following example, all files were copied 
to the root C drive.  Change your paths as necessary.  This example also uses powershell, but a cmd prompt would also work.

* Copy the correct Toec MSI for the architecture of the PC and the Toec-Transform.mst file to a location on the destination PC (c:\ in these examples).
* Open PowerShell as administrator  
[![](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall1.jpg){: style="height:150px"}](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall1.jpg)

* Change directory to the MSI location with the command ```cd c:\```
[![](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall2.jpg)](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall2.jpg)
* Install Toec with the following command:  

&nbsp;	

	.\Toec-1.1.0-x64.msi TRANSFORMS=Toec-Transform.mst

* After installation is complete, verify the Service installed and is running, in services.msc
[![](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall4.jpg)](https://theopenem.com/wp-content/uploads/2018/11/cmdinstall4.jpg)

!!! success "This Concludes Install Toec Via Cmd / PowerShell. Check this off of your Installation checklist now."	

