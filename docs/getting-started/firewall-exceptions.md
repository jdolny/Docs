# Firewall Exceptions
When the IIS Server Role was installed earlier, it automatically created an exception for port 80 and 443.  Two more exceptions must be added 
for the additional Web Applications, port 8080 and port 8888.  While we are here we will also setup ports 8443 and 4444 should you decide 
to enable SSL at a later time.

###### 1. Go to **start or run** and enter **wf.msc**

---

###### 2. Select **Inbound Rules**, **Right click** on **Inbound Rules** and select **New Rule**
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/firewall-step01.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/firewall-step01.jpg)

---

###### 3. For the **Rule Type**, select **Port**
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/firewall-step02.jpg){: style="height:150px"}](https://theopenem.com/wp-content/uploads/2018/11/firewall-step02.jpg)

---

###### 4. On the protocols and ports page, select **TCP** and ports **8080,8443**
  
  [![](https://theopenem.com/wp-content/uploads/2018/11/firewall-step04.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/firewall-step04.jpg)

---

###### 5. On the **Action page**, select **Allow the connection**.

---

###### 6. On the **Name** page, enter **Toems-API**, click Finish

---

###### 7. Follow Steps 2-6 again to create an exception for Toec-API

* This time use ports **8888,4444** and set the name to **Toec-API**

---

!!! success "This concludes the Create Firewall Exceptions.  Check this off of your Installation checklist now."