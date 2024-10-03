
## Code setup

The code is stored here:

In order to run the code locally you will need to:
- Clone
- Open in Visual Studio
- Change branch to {third branch}
- Go to ProctorAdminController.cs
  ![[Pasted image 20240930104545.png|600]]
  - Comment out the following code and uncomment the test request.
  ![[Pasted image 20240930104726.png|800]]
  - Hit start. 
  - You will be directed to the moderation dashboard.
## App Service setup

This App Service is used to embed the Proctorio Wrapped aNS page. 
- Navigate to the `Production@newleaftech.co.za` account on the [Azure Portal](https://portal.azure.com/) 
- Search for `App Services`
- Create a new App Service called `{clientname-proctor}`
- Create a new Resource Group with `RG-{CLIENTNAME}` naming convention if the client does not have an existing RG, else select clients RG.
- Create a new App Service Plan with `ASP-{CLIENTNAME}-PROCTOR` naming convention. 
	- Usually Standard S1 tier is sufficient to start off with depending on the number of concurrent examinations to be proctored this can be increased or decreased. 
- See example setup below: 
![[Pasted image 20240318112527.png|800]]
	
  
---
## Moderation email Azure Function
- This is dependant on client needs and not all clients require this functionality.
- This function is two fold:
	- It is used to send emails to Moderators as newly proctored assessments are submitted.
	- It is used to send emails to candidates who have been approved, notifying them that they may login to aNS and download their certificate.

---
## Deployment 
Currently each Client has their own Proctorio project due to different requirements e.g. differing LMS etc. 
- This source code is for the ASP.NET web application that is hosted in the Azure App Service.
- The source code for this project can be found on Azure DevOps by searching the `NewLeafDevelopment` organisation for `Proctorio`. 
- Make sure to update the app service URL in source code where it may be hard-coded? 
  
  ![[Pasted image 20240318110546.png|800]]
  https://dev.azure.com/NewLeafDevelopment/
- Clone the Source code to your local machine and open in Visual Studio. 
- Change CI of website such as logos and colours to suite client requirements. 
- Change the connection string in the `Web.config` file to point to the newly created Proctor database. 
- Right click the Project and select `Publish`. 
- Follow publish steps and select the App Service created in the previous steps.

---