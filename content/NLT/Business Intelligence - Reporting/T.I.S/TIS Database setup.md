# Overview
The TIS database is a MSSQL database that we host on the Azure MSSQL server: ==sqls-nltintegration-prod.database.windows.net== unless otherwise required by the client. 
Clients that have their own MSSQL servers are:
- Wellness Warehouse
- Exxaro
- GIFs

A general TIS database has the following tables in it: 
![[Pasted image 20240312095526.png|800]]

In order to standardise the TIS system we generally create a .DACPAC file of an existing client DB. This DACPAC will contain the schemas, types and programmabilty of the existing database without any of the data in it. 

Below are the steps to create a database for a new TIS client:
1. Connect to the ==sqls-nltintegration-prod.database.windows.net== server. 
2. Create a new Database with the following naming convention: {CLIENTNAME}DB.  **Might be done via restore DACPAC? need to dbl check**
3. Export the DACPAC.
4. Restore the DACPAC onto new DB.
5. Change the DB type on azure portal to be basic or standard.
6. Login to aNS environment and get the API key.
7. Encrypt the API key.
8. Insert the configuration details into config table
```sql

```
9. Insert configuration in syncLoop table.
10. Run local testing of Azure function as described in step 3 here: [[TIS Sync Function setup]] to see if data is synchronised into the database.

>[!Note]
>It's important to note that there needs to be at least one learner in the DB for the sync to run correctly.
>Usually I will place a breakpoint at this point in the code, however you may insert a random learner into the DB to get this working as a work around. 
>
