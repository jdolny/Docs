# Install IIS

!!! success "Start filling in the the Server Topology Worksheet under Application Server 1 now.  Provide the FQDN and server version."
###### 1. Begin by opening **Server Manager**

  [![](https://theopenem.com/wp-content/uploads/2018/11/step00.jpg){: style="height:350px"}](https://theopenem.com/wp-content/uploads/2018/11/step00.jpg)

---
###### 2. Select **Manage**, then **Add Roles and Features**

  [![](https://theopenem.com/wp-content/uploads/2018/11/step01.jpg)](https://theopenem.com/wp-content/uploads/2018/11/step01.jpg)

---
###### 3. Continue to click Next until you get to the **Server Roles** page.  Select **Web Server (IIS)** and click **Next**.

  [![](https://theopenem.com/wp-content/uploads/2018/11/step02.jpg)](https://theopenem.com/wp-content/uploads/2018/11/step02.jpg)

---
###### 4. On the **Features** page, expand **.NET Framework 4.7 Features**, select **ASP.NET 4.7**, click **Next**.  

!!! warning "This may display .NET Framework 4.6 or 4.5 Features on older Server versions."

  [![](https://theopenem.com/wp-content/uploads/2018/11/step03.jpg)](https://theopenem.com/wp-content/uploads/2018/11/step03.jpg)

---
###### 5. On the **Role Services Page**, scroll down to **Application Development and check the box**.  Expand the selection and select **ASP.NET 4.7**, this automatically selects the other options for you.  Then click **Next**, and finally **Install**.

!!! warning "This may display .NET Framework 4.6 or 4.5 Features on older Server versions."

  [![](https://theopenem.com/wp-content/uploads/2018/11/step04.jpg)](https://theopenem.com/wp-content/uploads/2018/11/step04.jpg)

---

!!! success "This concludes Install IIS With Web Application Development Support.  Check this off of your Installation checklist now."