# Overview
The BI-Embed project is an Azure-hosted Dynamic Power BI Dashboard Redirector. It is a web application deployed on Azure App Service called 'learning-analytics', designed to seamlessly integrate with Learning Management Systems (LMS) such as aNS. The primary function of this application is to dynamically generate Power BI (PBI) report URLs based on Learning Tools Interoperability (LTI) requests received from the aNS LMS.

>[!Note]
>This is a long running application and usually does not need any interventions as new clients are on-boarded as it is configured via the NLTADMINDB itself.

**Key Features:**

1. **Azure Integration:** The software is hosted on Azure, utilizing the Azure App Service.
2. **LTI Request Handling:** Upon receiving an LTI request from aNS via an external activity called 'Training Intelligence', the application extracts relevant information to identify the user and their associated learning environment.
3. **MSSQL Database Interaction:** The application interfaces with an MSSQL database called NLTADMINDB which is hosted on Azure to retrieve specific environment and report data related to the user's learning environment and reports. This data forms the basis for dynamically constructing the Power BI report URL.
4. **Dynamic URL Formation:** Using the extracted information from the LTI request and the data retrieved from the NLTADMINDB database, the application dynamically forms a Power BI report URL tailored to the user's learning context.
5. **User Redirection to PBI Dashboard:** The user is then redirected to the dynamically generated Power BI report URL, where they have access to their personalized T.I.S dashboard.

# Location
The source code for this project can be found at: https://dev.azure.com/NewLeafDevelopment/NLT%20TIS%20Access
