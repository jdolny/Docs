# Test The Web Applications
Now is a good time to test the 3 web applications before continuing on.  These tests are all done through your web browser, and should be done from a 
remote computer to test the firewall rules as well.  Your Theopenem server should now be reachable by the server’s FQDN and corresponding port.  

!!! info "In these examples the server name is toems-01.theopenem.com and should be replaced by your actual server name."

###### 1.  Test Toems-API (Backend)
* Open a web browser
* Navigate to http://toems-01.theopenem.com:8080/Setting/VerifyDb
* The page should respond with the number 60
* If this step was successful the Toems-API is running and can access the database

---

###### 2.  Test Toec-API (Client connections)
* Open a web browser
* Navigate to http://toems-01.theopenem.com:8888/Provision/VerifyDb
* The page should respond with the number 60
* If this step was successful the Toec-API is running and can access the database

---

###### 3.  Test Toems-UI (Frontend)
* Open a web browser
* Navigate to http://toems-01.theopenem.com
* You should be greeted by the login page
* Login With:
> **Username:** toemsadmin  
> **Password:** toemsadmin
* If this step was successful the Toems-UI is running and can communicate with Toems-API.  **Do not attempt to configure anything in the Toems-UI yet.**  Close your browser.

---

!!! success "If any of these 3 tests failed, revisit all sections up to this point, looking for any discrepancies, otherwise, Testing The Web Applications Is Complete.  Check this off of your Installation checklist now."

