# Install Certificates
The certificates are used for identification, encryption, and signing with your endpoints.  The CA and intermediate need to be imported into the Windows Certificate Store
on each Theopenem server.

###### 1. Export Certificates from Toems-UI
* Login to the Toems-UI from the server itself, do not do this remotely, these certificates are being installed on the Application Server itself, not an end user’s PC.
* Select Admin Settings from the Navigation Menu
* Select Certificates from the Sub Navigation Menu
* Find the certificate with the Type Authority and click Export
* Save the File when prompted
* Locate the file that was just downloaded and rename it to toems-ca
* Find the certificate with the Type Intermediate and click Export
* Save the File when prompted
* Locate the file that was just downloaded and rename it to toems-intermediate
* You should now have the 2 certificates saved on the local server
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-01.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-01.jpg)

---

###### 2. Install Certificates in the Local Certificate Store
* Double click on the toems-ca file, select Install Certificate
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-02.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-02.jpg)
* Select Local Machine, click Next
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-03.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-03.jpg)
* Select Place all certificates in the following store, click Browse, select Trusted Root Certificate Authorities, click OK, then Next, then Finish
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-04.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-04.jpg)
* Perform the previous 3 steps on the toems-intermediate certificate, this time when selecting the location to store the cert, select Intermediate Certification Authorities
[![](https://theopenem.com/wp-content/uploads/2018/11/certs-05.jpg)](https://theopenem.com/wp-content/uploads/2018/11/certs-05.jpg)

!!! info "Remember to copy the 2 certificates to any other servers running the Toec-API and complete section 2 on each other server"

!!! success "This concludes Install Certificates.  Check this off of your Installation checklist now."