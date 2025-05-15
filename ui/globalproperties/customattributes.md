# Custom Attributes
Custom attributes are used to add extra information to your computers that you may want to keep track of.  Examples might include, asset tag number, windows product key, computer building name or room, etc.  
After creating the custom attribute you will find it now exists under the Custom Attributes page of each computer, where you can populate the info related to that computer.

## Search
The search page allows to view and delete existing custom attributes. Filtering options include:
<br/>
* Search by custom attribute name

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes the selected custom attributes.

<br />
<br />

## New

Field | Description
------|------------
Name | The name of the custom attribute, names must be unique and contain only alphanumeric characters, space, underscore, or dash.
Description | The description field is optional for you to give a short description for what the custom attribute is used for.
Text Mode | This field is used to specify how much data you plan on submitting with this attribute. The SingleLine option is used for a small amount of data, such as serial number. The MultiLine option is for something larger, such as a description field.
Available To Imaging Client | If you want to access the data during imaging, enable this and you can reference it by using a dollar sign in front of the name, such as $asset_tag

#### Actions
Action | Description
------|------------
Add Attribute | Creates the attribute defined on the page.

<br />
<br />

> [!NOTE]
> The following additional pages are available after a schedule is added or when selecting the view button on a specific schedule from the search page.

## General
This page is used to edit the attribute with the same options as when it was created. 

#### Actions
Action | Description
------|------------
Update Attribute | Updates the custom attribute.
Delete Custom Attribute | Permanently deletes the custom attribute.

<br />
<br />

