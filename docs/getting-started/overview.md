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

## Topology
Theopenem is a fully redundant and scalable application.  Basic users can simply install everything on a single server.  If you are more advanced or want more control over your system, you could do something like the example below.  There is no limit to the number of servers you can use.

- **Application Server 1** - This application server runs all 3 required web applications.
- **Application Server 2** - This application server runs all 3 required web applications.
- **Database Server** - Runs the backend database that both the Toems-API and Toec-API communicate with.
- **File Share** - When more than one Toec-API or Toems-API server is installed, data replication must occur b/w the servers.  An SMB file share is used for this purpose.  The Toec agent does not communicate with this server.  You can use any existing File Server for this purpose.  If only a single Toec-API and Toems-API are used in your topology, the File Share is not needed.
- **DMZ Toec-API (Optional)** - A Toec-API server can be setup in your DMZ to allow management of endpoints when they are offsite.  This server should only run the Toec-API, you should never allow Toems-API or Toems-UI access from the outside.
 
!!! info "Each application server should be dedicated to Theopenem and not shared with other web applications or services.  The database server and file share can be on shared resources."
 
In the model outlined above, it gives you load balancing as well as failover capabilities.  You can take down either Application Server for maintenance with no effect on your endpoints.  When using multiple Toems-API and Toems-UI servers, you can load balance the requests through DNS or a Load Balancing Appliance.  
!!! danger "The Toec-API should never go through a load balancer.  Load balancing and failover of the Toec-API is built into the Toec agent.  Running the Toec-API through a load balancer could lead to authentication failures."
The diagram below shows the traffic flow among these services.

[![](https://theopenem.com/wp-content/uploads/2018/11/Recommended-Install.jpg)](https://theopenem.com/wp-content/uploads/2018/11/Recommended-Install.jpg)