# Overview
This is an Azure Function App which is hosted on Azure. The Function App contains multiple timer based functions which are used to connect to the aNewSpring API, pull data and store that data in an Azure MSSQL Database. 

They currently pull data related to:
1. Learners
2. Templates, Courses, Activities
3. Subscriptions
4. Groups (*Optional*)

This data is then processed and compared to the existing data in the Azure MSSQL database. If there is a mismatch of data, then data will be Created/Updated/Deleted accordingly. 

---
# Setup 
## 1. Create Azure Function App

1. To begin, navigate to the Function App service on https://portal.azure.com (Log in using the Production credentials). 
   This can be done by selecting the below icon or searching for Function App in the search bar. 
![[Pasted image 20240310093046.png|800]]

2. Click the 'Create' button
![[Pasted image 20240310093407.png| 800]]

3. Here we will fill in the relevant information. Generally we follow the naming convention of 'BI-{client name}-prod' for name and use the RG-TISFUNCTIONS-PROD 
   resource group. Make sure to select .NET and version 4.8 as the runtime and place the resource in the South African North Region. It is also important to select the 
   Consumption plan to reduce costs.
![[Pasted image 20240310095627.png|800]]

4. On the Storage tab we can set the 'storageacctis' account.  
![[Pasted image 20240310100051.png|800]]

5. Click 'Review + create' button to create the Function App.
6. Navigate to the resource, select the 'Change App Service plan' tab under 'App Service Plan' and set the destination plan to 'SouthAfricaNorthPlan'.
![[Pasted image 20240310100707.png|800]]
### 1.1 Configure Azure Function App 
In order for the function app to know which database and client API to connect with we need to configure some settings on the function app itself. 

The way that this Function App knows which aNewSpring environment it needs to connect to and sync data from is by connecting to the client's database on the Integration Server. 
It gets the encrypted API key from that client's Environment table, pulls it into the function and decrypts it using the Prefix given. 

Due to wanting to have a single code base for the synchronisation function, the configuration of the Prefix and Connection String is done on the Function App itself in Azure.
We do this by creating two Environment Variables as seen below:
![[Pasted image 20240403141914.png|1000]]

>[!Note] 
>These variables must be named exactly as depicted above. 
>The connection string can be obtained from the source code and should be updated to point to the new database that is created for the new client.
>The API Key can be retrieved from the aNewSpring environment under the settings tab.
## 2. Retrieve project source code
1. Navigate to devops project: https://dev.azure.com/NewLeafDevelopment/_git/TIS_Sync_Function.
2. Open Project in Visual Studio using .sln file. 
3. Add settings.local file:
## 3. Local Testing

>[! NOTE: ]
>This assumes the following:
>1. The Function App is configured with the correct connection strings and prefixes.
>2. The database is in place for the desired client.

Once all is configured, we can now open the project source code within Visual Studio 2019. From here we will update the local.settings file and use the correct configuration variables(these are the same as the ones used to configure the Function App), this is so that we can test locally without having to deploy the functions to Azure. 

- Copy code from Learners and paste into HTTP trigger function. 
- Make Postman request.
- View database to see if data has been synchronised.
- Repeat for other functions.
- Order to run functions is generally as follows:
	- Learners.
	- Courses.
	- Subscriptions.
## 4. Deployment
1. Make sure all required functions are not commented out.
2. In Visual Studio code, right click on project name and select 'Publish'.
3. Login to production@newleaftech.co.za.
4. Select Resource Group.
5. Select Function App created for that client.
6. Click 'Publish'
>[!Note]
>You will need to set the `SCM Basic Auth` option under Configuration->General Settings in order to successfully publish the function app.
>![[Pasted image 20240403141704.png|1000]]



TODO: 
	- Get screenshots from VS on windows machine

[[TIS Database setup]]
