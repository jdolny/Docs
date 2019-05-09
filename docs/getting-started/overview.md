# Overview
This server installation guide will provide a complete walk through for the setup of Theopenem server (Toems) components.  These components include the **Toems-UI**, the **Toems-API**, 
the **Toec-API**, and **database**.
  The installation of the endpoint agent (Toec) will be covered in the Client Installation Tutorial.  If you have not yet read the [Welcome Introduction](/), please read it before 
  continuing, also before starting this guide, ensure you have downloaded the **Installation Checklist** and **Server Topology documents**.  Fill out the documents as you move forward through 
  the guide.

!!! info "Installation Documents Downloads"
	[Installation Checklist](https://theopenem.com/wp-content/uploads/2019/01/Theopenem-Checklist.docx)  
	[Server Topology](https://theopenem.com/wp-content/uploads/2019/01/Theopenem-Server-Topology.docx)
	
This guide is fairly lengthy and may seem wordy for anyone with Web application / database experience.  As you may have noticed, there is no automated installer for Toems.  This 
forces you to learn some of the fundamental concepts of Theopenem and will enhance your troubleshooting capabilities.  An experienced Theopenem user can setup everything 
up in about 20 minutes.  If this is your first time installing Theopenem, allow yourself 2-3 hours to complete this guide.

## Prerequisites
- Install .NET 4.6 **(Only required if your server version is Server 2012R2.  Newer server versions already have a greater version of .NET installed)**.  
.NET 4.6.2 can be [downloaded here](https://dotnet.microsoft.com/download/thank-you/net462).  If you wish to install a newer version of .NET greater than 4.6, that is fine also.
- Optionally download and install [Notepad++](https://notepad-plus-plus.org/download/v7.6.2.html).  Though not required, it will prove helpful when modifying the appropriate config files in the upcoming sections.

!!! success "This Concludes the Prerequisites. Check this off of your Installation checklist now"