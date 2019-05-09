# Create Database Firewall Exceptions
!!!info "This section is only completed a single time on your database server."

If your database was installed on a remote server in relation to your Theopenem server, you will need to open the firewall on that database server to allow connections from all Toems-API and Toec-API servers.
<br><br>

>Follow the [Creating Firewall Exceptions](/getting-started/firewall-exceptions/) Guide from earlier, modifying the ports as necessary.

* If using MS SQL Server you need to allow port 1433
* If using MariaDB you need to allow port 3306

&nbsp;

!!! tip "For enhanced security you should only open the firewall for your Theopenem Server IP addresses, not any IP address"

!!! success "Check off Create Database Firewall Exceptions from your installation checklist now."