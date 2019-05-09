# Database Overview

!!!info "This section is only completed a single time, even if you are installing multiple Theopenem servers.  All Toems-API and Toec-API applications share the same database."

<br>
Theopenem supports Microsoft SQL Server, MariaDB, and MySQL.  There is no functional difference in how they are used with Theopenem.  Choose the RDBMS you are most comfortable with.

!!!danger "Remember, SQL Server Express is not supported"  

<br>
The following guide serves as a baseline to get the database running on either MariaDB or Microsoft SQL Server.  

* If you already have an existing database cluster, it is recommended to use it.  
* The guides may need adapted to fit your environment.  
* If you are installing a new database server, it's recommended to install it somewhere other than your Theopenem server.
* If required, it is acceptable to install the database on Theopenem but should really only be done as a last resort and if only a single Theopenem server is deployed

!!!success "Continue filling in the Server Topology Worksheet under Database Server.  Fill in the Server FQDN, RDBMS, and RDBMS Version"

> [Continue With MariaDB](/getting-started/database-mariadb)  
> [Continue With SQL Server](/getting-started/database-sqlserver)