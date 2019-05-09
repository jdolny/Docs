# Welcome
Welcome to The Open Endpoint Manager, a solution that provides a full suite of Windows management capabilities as well as computer inventory, custom asset management, 
and reporting.  Theopenem is an on-premises solution, all servers and data remain within your organization.  In terms of features and capabilities, it resembles products 
such as SCCM, PDQ, Desktop Central, KACE, and the list goes on.  For a full list of features, check out https://theopenem.com/features.


## How It Works

Like many software applications, Theopenem consists of a Server side application and a Client side application.  The Server side application ("Toems") was developed using 
C# and the .NET framework.  This enables easy installation on Windows Servers with IIS.  Toems consists of three separate Web Applications that scale to meet the needs of 
any size organization.  By separating the Server components into 3 Web Applications, this provides maximum flexibility and security by only exposing the required components 
to the correct people or endpoints.  The Client agent application ("Toec") is a Windows Service that is installed on each endpoint you wish to manage.  The agent is available 
in both 32 and 64 bit MSI format to enable simple deployment using GPO, cmd line install, or any other deployment application that supports MSI's.  The use of an endpoint agent, 
gives the greatest amount of control and reporting over the endpoints without the need to enable SMB shares or ADMIN shares.  All communication b/w the client and server use the 
HTTP or HTTPS protocols.  After Theopenem Servers and Endpoints are installed and configured, they will check-in with the Server on a predefined customizable schedule (60 minutes 
by default).  Upon check-in, the server will return any policies that are applicable to the Endpoint at that moment.  The client will run the policies and then check-in with the 
server in another 60 minutes to see if any new policies have been added.  Therefore an endpoint is constantly looking for policies to run on an interval schedule defined by the server.  If a policy needs to run immediately, A Theopenem administrator can force the endpoints to check-in at any time, instead of waiting for the next check-in interval to elapse.


## Server Requirements (Toems)
### Hardware
- **CPU** requirements align with the requirements of the OS
- **Solid State Disks** are recommended by not required, storage capacity should align with the OS requirements plus enough to store the applications that will be deployed.
- **Memory** is the most difficult requirement to assess.  It depends on many factors, such as how many Servers will be used to distribute the load, if the database is local or remote, the amount of endpoints within the organization, and the number of policies defined in Theopenem.  8GB is typically enough with 16GB (possibly more) of memory being the recommended number.


### Software
The following operating systems are supported: 

- **Server 2012R2**
- **Server 2016**
- **Server 2019**

!!! info "Note"
	Toems requires a 64-bit Windows Server OS with .NET Framework 4.6 or newer installed.

## Database Requirements
Theopenem supports the following databases:

- MariaDB 10.2 or greater
- MySQL 5.7 or greater
- Microsoft SQL Server 2012 or greater

If you have an existing database cluster with any of the above mentioned applications, you can use it.  Otherwise, you can create a new server, 
either on your Application Server or a separate server.  The database server should have a minimum of 8 GB ram.

!!! info "A database that's run on a server that is separate from Theopenem is recommended"

!!! danger "SQL Express is not supported."
 
## Client Requirements (Toec)
Supported OS's include:

- **Windows 7**
- **Windows 8/8.1**
- **Windows 10**

Toec can be installed on both 32-bit and 64-bit architectures.  Like Toems, it also requires .NET framework 4.6 or newer be installed on the OS.
There are no specific CPU, Hard Drive, or Memory requirements.
 
## Bandwidth Requirements / Network Impact
Determining the impact on your network also varies depending on your individual Theopenem setup.  Factors such as the number of endpoints, how often the endpoints check-in, the number of Servers, and the number of polices and modules defined in Theopenem all contribute to the impact on the network.  The following example demonstrates the data utilized from a single endpoint.
 
A new endpoint registers with Theopenem, all required certificates are exchanged and an encryption key is exchanged b/w server and endpoint.  The total data sent from the client to the server and back to the client is approximately 14KB.
An hour later the endpoint checks-in and has found 3 active policies.  The policies are set to run an inventory scan, start tracking user logins, and start tracking application usage.  The total data transferred is approximately 70KB, this number will vary depending on the size of the inventory scan.
An hour later the endpoint checks-in again and no active policies are found.  This time only approximately 5KB are transferred.
 
This means that registering a new endpoint and scanning it's inventory only uses about 100KB, and 5KB every hour after that, assuming no more policies need to run.  To put this in perspective, a single visit to Google with no caching, at the time of this writing was approximately 400KB.
 
To summarize, the amount of data transferred by Theopenem on an hourly bases, is typically less than a user loading a single web page.  However, this changes significantly if a policy is deploying a software application.  When deploying software, the full size of the application will be transferred, this could be in the hundreds of MB or even GB.  To mitigate network problems with large software deployments and a large number of endpoints, Theopenem has built-in throttling.  Each Theopenem server can have a maximum number of connections as well as a maximum bitrate per connection.  Each server can have different values providing flexibility depending on the power of that specific server.  As a final example, A Theopenem server could set a maximum of 20 connections at 5Mb per connection, limiting the network performance of that server to 100Mbps.
 
## Endpoint Impact
The Toec service continuously runs in the background on the endpoint.  While idle, it typically uses b/w 30MB and 50MB of RAM.  It will increase depending on actions needed by the policy and will eventually stabilize back to around 30MB and 50MB.  An additional application named Toec-UI will also run for each user at login.  This is required to run policies at user login or send messages to the endpoints.  This application typically uses around 10MB of RAM.
 
## AntiVirus
It may be necessary to whitelist the installer MSI for the Toec agent or even the directory for Toec after it's installed.  Toec is installed in c:\program files\toec.  If Toec is not functioning properly, be sure your antivirus solution isn't blocking anything.
 
## Security
Theopenem was designed with security in mind.  While no product is invulnerable to attackers, it was designed using various implementations of industry standards such as OAuth 2.0, HMAC authentication, Certificate authentication and encryption.  The Server is comprised of 3 separate Web Applications allowing you control over which components should be accessible to what users.  For example, the management of Theopenem is contained within the Toems-UI and Toems-API.  These two applications can be firewalled off to only users that need access to the system.  The endpoints only ever need to communicate with the Toec-API.  Authentication to the Toems-API is achieved through OAuth 2.0 bearer tokens which are only valid for 1 hour, in addition, users are locked out for 15 minutes after too many failed login attempts, mitigating brute force attacks.  The body of all communications b/w the client and server are encrypted using a combination of device certificates and encryption keys.  If SSL is setup on the Web Servers, the headers will also be encrypted, as well as the body for a second time.  Commands from the server to each endpoint are signed using a CA-Intermediate-Device Certificate chain ensuring the client will only run commands originating from your servers.
 
## Recommended Topology
The recommended server topology involves the use of 5 servers.  It's just a recommendation, you can run everything off a single server if you must, or anything in between.

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
