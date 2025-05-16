# Debugging

There are times where you may need additional logging to help troubelshoot a problem.  You can place each web application and Toec agent into debug mode.

<br />
<br />

## Server Debug
The log level for each server application is set in the web.config file for each application.  You should only need to change the log level for the Toec-API and Toems-API applications.
* Scroll down towards the bottom of the file and find the line that says ```<level value="INFO">```
* Change it to DEBUG as pictured below<br/>
![](/latest/images/debug-1.png)


<br />
<br />

## Client Debug
Toec can be set to Debug mode by running the following command on the client computer you want to debug Toec on.  The command is case sensitive.
* Ran From the Toec directory<br />
```Toec.exe --logLevel DEBUG```<br/>
![](/latest/images/debug-2.png)







