# Users
A user is anyone that will be managing Theopenem.  They are not the endpoint users.

## Search Users
The search page displays the list of current users. Filtering options include: <br/>

* Search by name

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes the selected users.  Administrators cannot be deleted.  You must change their role to a user first.

<br />
<br />

## New User

Field | Description
------|------------
User Name | The name the user will use to login with.
User Role | The role of the user, administrators have full access to Theopenem. The user role can be assigned various permissions through ACL's after they have been added.
Use LDAP Authentication | When enabled, the user will authenticate against AD instead of the local Theopenem database. When using this feature, the username must match the samAccountName in AD and the LDAP connection must be setup in Admin Settings->LDAP.
User Password | The password for users that are not using LDAP Authentication. A user can change their password from the User's navigation menu after logging in. A password must be at least 8 characters.
Email | An email address for the user to receive notifications. Email must first be setup in Admin Settings->E-mail before emails will work.
Theme | Sets the theme for the user. If the user is currently logged in, a logout is required to apply the theme.
Default Computers Page | The default page to load when clicking on Computers from the navigation menu.
Default Computer Sort | The default way to sort computers when clicking on Computers from the navigation menu.
Default Login Page | The default page to go to after logging in.
Enable Web MFA | Require the user to use MFA when logging into the web portal.
Enable Imaging MFA | Require the user to use MFA when logging into the imaging client.  To use this feature, append the code to the end of the password.

#### Actions
Action | Description
------|------------
Add User | Creates the user.

<br />
<br />


## Search User Groups
The search page displays the list of current user groups. Filtering options include: <br/>

* Search by name

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes the selected user groups.

<br />
<br />

## New User Group

Field | Description
------|------------
Group Name | The display name of the user group.
Group Role | The role that will be assigned to any users added to the group, administrators have full access to Theopenem. The user role can be assigned various permissions through ACL's after they have been added.
Use LDAP Group | When enabled, users from the specified AD security group are automatically added to the system. This is not a sync. The user will be added when they successfully authenticate. The user will authenticate against AD instead of the local Theopenem database. When using this feature, the LDAP connection must be setup in Admin Settings->LDAP.
LDAP Group Name | This field is only available when Use LDAP Group is enabled. This is used to specify the name of the AD Security Group to match against.


> [!NOTE]
> The following additional pages are available after a users is added or when selecting the view button on a specific user from the search page.

## General
The general page can be used to update the general information about the user.

Field | Description
------|------------
User Name | The name the user will use to login with.
User Role | The role of the user, administrators have full access to Theopenem. The user role can be assigned various permissions through ACL's after they have been added.
Use LDAP Authentication | When enabled, the user will authenticate against AD instead of the local Theopenem database. When using this feature, the username must match the samAccountName in AD and the LDAP connection must be setup in Admin Settings->LDAP.
User Password | The password for users that are not using LDAP Authentication. A user can change their password from the User's navigation menu after logging in. A password must be at least 8 characters.
Email | An email address for the user to receive notifications. Email must first be setup in Admin Settings->E-mail before emails will work.
Theme | Sets the theme for the user. If the user is currently logged in, a logout is required to apply the theme.
Default Computers Page | The default page to load when clicking on Computers from the navigation menu.
Default Computer Sort | The default way to sort computers when clicking on Computers from the navigation menu.
Default Login Page | The default page to go to after logging in.
Enable Web MFA | Require the user to use MFA when logging into the web portal.
Enable Imaging MFA | Require the user to use MFA when logging into the imaging client.  To use this feature, append the code to the end of the password.

#### Actions
Action | Description
------|------------
Update User | Updates the user's general information.
Reset Mfa Data | Clears the MFA secret for the user in the case they have lost their Authenticator.  The user will be prompted to setup again at next login if MFA is enabled.
Remove Legacy Group Data | The way that user groups are handled was changed in version 1.5.4.  If your user is incorrectly assigned to groups, use this option to clear the old data and use the new groups.
Delete User | Permanently deletes the current user.

## Access Control

This page is used to set the permissions for the user. It has no effect if the user is in the administrator role. The permissions are mostly self explanatory, following the general navigational layout of Theopenem. The options listed here
apply to every computer / image in Theopenem.  If you want a user to only have permissions to specific computers or images, you can set that up in the user groups page.

#### Actions
Action | Description
------|------------
Update Access Control | Updates the user's permissions.
Delete User | Permanently deletes the current user.

## History

Displays a list of filterable actions that the user has performed in Theopenem. Currently not everything is tracked, but most are and will continue to be expanded in future versions.


> [!NOTE]
> The following additional pages are available after a user group is added or when selecting the view button on a specific user group from the search page.

## General
The general page can be used to update the gernal information about the user group.

Field | Description
------|------------
Group Name | The display name of the user group.
Group Role | The role that will be assigned to any users added to the group, administrators have full access to Theopenem. The user role can be assigned various permissions through ACL's after they have been added.
Use LDAP Group | When enabled, users from the specified AD security group are automatically added to the system. This is not a sync. The user will be added when they successfully authenticate. The user will authenticate against AD instead of the local Theopenem database. When using this feature, the LDAP connection must be setup in Admin Settings->LDAP.
LDAP Group Name | This field is only available when Use LDAP Group is enabled. This is used to specify the name of the AD Security Group to match against.

#### Actions
Action | Description
------|------------
Update User Group | Updates the user group's general information.
Delete User | Permanently deletes the current user group.

## Access Control

This page is used to set the permissions for all members of the group. It has no effect if the group is in the administrator role. The permissions are mostly self explanatory, following the general navigational layout of Theopenem. There are also some more specific options below the first section.

#### Actions
Action | Description
------|------------
Update Access Control | Updates the user groups permissions.
Delete User Group | Permanently deletes the current user group.

## Image Management

If image management is enabled, the Access control permissions for all related image settings is only enabled for the images the user group has permission to use.  The user will not have any access to images that are not selected.

#### Actions
Action | Description
------|------------
Update Image Management | Updates the image management settings.
Delete User Group | Permanently deletes the current user group.

## Computer Group Management

If computer group management is enabled, the access control permissions for all related computers and groups is only enabled for the groups and group members that the user groups has permission to use.  The user will not have any access to groups or computers in the groups that are not selected.

#### Actions
Action | Description
------|------------
Update Group Management | Updates the group management settings.
Delete User Group | Permanently deletes the current user group.

## Add Members
If the group is not an LDAP group, group members are added from this page.

## Current Members
if the group is not an LDAP group, members and listed and removed from this page.