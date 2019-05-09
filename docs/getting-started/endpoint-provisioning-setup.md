# Endpoint Provisioning Setup

Provisioning is the process of allowing an endpoint to be managed by Theopenem.  This includes the exchange of certificates and encryption keys b/w the client and server.  This 
process is automated when the Toec Agent is installed, but there are some settings on the Server that should be addressed to ensure a smooth provisioning process.

###### 1. Active Directory Sync
Syncing with Active Directory is highly recommended but not required.  It is a read only one way sync from AD to Theopenem.  It will sync in Computer names and 
Organizational Unit names, servers are skipped.  The benefit of syncing in the Computers is to pre-provision them.  A pre-provisioned computer is added to Theopenem 
but cannot yet be managed until provisioning from the client completes.  When a computer is pre-provisioned, it can be assigned to groups with policies already defined, 
this way when an endpoint completes the provisioning process, it will automatically start running the necessary policies.  Syncing from AD also allows you to assign 
policies to your existing OU's, as another method of targeting groups of computers.  If you skipped over the LDAP setup during the server installation it's recommended 
to configure it now.

* Login to the Toems-UI, select Admin Settings->Security
* Enable the LDAP Integration if not already enabled
* Click Actions, Update Security Settings
* Select Admin Settings->LDAP
* Fill out the LDAP form, use the built-in help menu in the top right for more info on the fields
* Click Actions, Update LDAP Settings
* Click Actions, Test AD Bind, to verify the connection was successful
* Select Admin Settings->Task Scheduler
* Find the LDAP Sync row and click Run Now.  There is no visual confirmation when using the Run Now button.  By default this task will run every night at 1:00AM.  
Give the process 5-10 minutes to run, you can navigate away from the page.
* Select Computers->Search All.  It should show all of the synchronized computers with a Provision Status of PreProvisioned.
* Select Groups->Active Directory OU Browser.  You should see your Domain Directory Tree.

---

!!! success "This Concludes Active Directory Sync. Check this off of your Installation checklist now."

---

###### 2. Provisioning Security
There are a few security measures in place to regulate endpoint provisioning.  They are currently all on by default, but you may disable them.  The 
following options are available in Admin Settings->Security.


* **Preprovision Required** – When this option is enabled, a computer will not be allowed to provision unless it has already been pre-provisioned.  If you are syncing from Active 
Directory, computers have already met this requirement when they were synced.  If you are not syncing from AD, pre-provisions may be manually added from Computers->Create Pre-Provision.
* **New Computer Provision Approval Required** – When this option is enabled, a Theopenem user must manually approve computers before they will be allowed to provision.  This 
setting does not apply to pre-provisioned computers since they have already been approved.  Provision approval requests will be displayed in Computers->Approval Requests when a 
new computer tries to provision for the first time.  This is where the user can approve or deny the request.  A report is emailed twice per day when endpoints are waiting for approval.
* **Preprovision Approval Required** – This setting is a combination of the previous two settings.  When this is enabled, a user must manually approve and endpoint’s provision request 
even if it has already been pre-provisioned.  The request are still approved from Computers->Approval Requests, and a report is still sent twice per day.
