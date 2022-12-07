# Overview
This server installation guide will provide a complete walk through for the setup of Theopenem server (Toems) components.  These components include the **Toems-UI**, the **Toems-API**, 
the **Toec-API**, and **database**.
  The installation of the endpoint agent (Toec) will be covered in the Client Installation Tutorial.  If you have not yet read the [Welcome Introduction](/), please read it before 
  continuing. 
	
The installation process is mostly automated with the MSI.  The entire process should take about 20 minutes for you to complete.

## Prerequisites
- Install .NET 4.8.  
.NET 4.8 can be [downloaded here](https://dotnet.microsoft.com/download/thank-you/net48).  .NET 4.8.1 is also compatible.  .NET 5.0 and greater are not compatible.  They are fine if they are installed, 
but they will not serve as a substitute for .NET 4.8.x.
- Assign your server a static ip address

## Install Toems Web Applications

###### 1. Download the latest version of Theopenem from https://theopenem.com/downloads


---


###### 2. Run the installer
Most users should leave all of the default options selected during installation.  When asked for a local storage path, remember the location as you will need to enter that information in the web interface after installation.

---


###### 3. The Web Applications should now be installed.

---

!!! success "The next few sections are necessary to finalize and configure Theopenem"