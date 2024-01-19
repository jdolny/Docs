# Schedules
Schedules serve 2 purposes.
* They can be used for more granular control over a policy so the policy will only run on specific days and during specific times.  This could be useful if you didn't want an application
to deploy during peak hours.
* They can be used on a group to schedule automatic wakeup and shutdown of all computers in that group.

## Search
The search page allows to view and delete existing schedules. Filtering options include:
<br/>
* Search by schedule name

#### Actions
Action | Description
------|------------
Delete Selected | Permanently deletes the selected schedules.

<br />
<br />

## New
This page is used to create new schedules.  The options are self explanatory.  Select the days you want the schedule to run and the time.  It should be noted that 2 schedules will be required in order to function.
A schedule of when to start and a schedule of when to stop, both are then assigned to your Policy or Group.  The days of the week are only used on the start schedule, only the time is looked at for the stop schedule.
Also, the schedule is limited to 15 minute increments.

#### Actions
Action | Description
------|------------
Add Schedule | Creates the schedule defined on the page.

<br />
<br />

> [!NOTE]
> The following additional pages are available after a schedule is added or when selecting the view button on a specific schedule from the search page.

## General
This page is used to edit the schedule with the same options as when it was created.  There is one additional option.  A schedule can also temporarily be deactivated to disable it.

#### Actions
Action | Description
------|------------
Update Schedule | Updates the schedule with the options defined on the page.
Delete Schedule | Permanently deletes the schedule.

<br />
<br />

## Usages
The usages page allows you to easily determine which computers, groups, or policies the selected schedule applies to.

#### Actions
Action | Description
------|------------

Delete Schedule | Permanently deletes the schedule.

<br />
<br />