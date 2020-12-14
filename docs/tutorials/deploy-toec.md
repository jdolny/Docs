# Deploy Toec Via Group Policy

###### 1. Begin by copying your Toec 32 bit and Toec 64 bit files to a share that everyone has access to.
* This example uses the sysvol location on the domain controller.

[![](https://theopenem.com/wp-content/uploads/2018/11/gpo1.jpg){: style="height:150px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo1.jpg)

---

###### 2. Open Group Policy Management for your Domain

---

###### 3. Right click on Group Policy Objects for your domain and select New
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo2.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo2.jpg)

---

###### 4. Give the new GPO a name such as Deploy Toec, click OK
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo3.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo3.jpg)

---

###### 5. Right click on the newly create GPO and select Edit
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo4.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo4.jpg)

---

###### 6. Expand Computer Configuration, Expand Policies, Expand Software Settings, Right Click Software Installation, select New Package
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo5.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo5.jpg)

---

###### 7. Navigate To the UNC Path of the files and select the Toec-1.0.0-x64 file.  Do not select the 32 bit file.
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo6.jpg){: style="height:250px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo6.jpg)

---

###### 8. Select Advanced on the Select deployment method dialog.
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo7.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo7.jpg)

---

###### 9. The properties dialog should appear, just click OK.

---

###### 10. You should be back at the Group Policy Management Editor, again right click on Software Installation, Select New then Package.

---

###### 11. This time select the x86 version of the Toec MSI from the same network location.

---

###### 12. Again Click advanced on the Select deployment method dialogs, the click OK.

---

###### 13. Select the Deployment Tab, then Click Advanced

---

###### 14. Uncheck the box for Make this 32-bit X86 application available to Win64 machines, click OK
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo10.jpg){: style="height:300px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo10.jpg)

---

###### 15. Select the Upgrades Tab, If there is anything listed, remove it.
[![](https://theopenem.com/wp-content/uploads/2018/11/gpo11.jpg){: style="height:200px"}](https://theopenem.com/wp-content/uploads/2018/11/gpo11.jpg)

---


###### 16. Close the Group Policy Management Editor

---

###### 17. Link the GPO to the OUs you want to deploy to. It should go without saying, to start small and expand.

---

















