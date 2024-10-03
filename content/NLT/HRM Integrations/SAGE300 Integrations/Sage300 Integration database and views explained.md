
# Overview 
The Integration database is where a lot of the heavy lifting occurs for the synchronisation between SAGE and aNS. 
There are a number of views that pull the 

# NLT Views

# Processing of data

### Creating new learners on ANS and how it syncs to SAGE
N/A - The employee sync is a one way synchronisation from the master system. Meaning that no employees are ever created on SAGE based on new learners being created on aNS.
Only the reverse is true. I.E a new Employee created on SAGE can/will become a new Learner on aNS. 
### Creating new employees on SAGE and how it syncs to aNS
- Employees can be Created or Updated on aNS as learners. 
- The Employee Views on the INTDB are used to determine which employees on SAGE should be created/updated as learners on aNS.

![[Pasted image 20240322105614.png]]

The new/updated employee is added on SAGE, this comes through in the NLT.View on the SAGEDB. 

From there the information is pulled/added into the relevant tables(in this case the `Employee.Employee` table) on the INTDB and flags `EmployeeANSStatusID`/`EmployeeANSUpdateFlag` are used to determine if this learner needs to be added or updated on aNS. 

The learners that are required to be created or updated are pulled into the INTDB views based on the flags in the table, which are used from the integrator software to get records that need creation/updating on aNS and will then send these to the aNS API to run the relevant operations. 

Once complete the flags on the INTDB tables will be updated thus clearing the INTDB views so the system registers that those records no longer need to be created or updated. 

### Creating new training dictionaries on SAGE and how it syncs to aNS
 This will create new Courses on aNewSpring in the same fashion as the employee process mentioned above. 
### Creating new courses on aNS and how it syncs to SAGE
N/A - Creating new courses on aNS will not create or update anything on SAGE. 

### Creating new Employee Training Transactions on SAGE and how it syncs to aNS
This is will subscribe the Learner to the corresponding course on aNS if both the Learner and the Course exist.

### Creating new subscriptions on aNS and how it syncs to SAGE
If you create/update a subscribtion on aNS it will get picked up in the INTDB views, from here the excel spreadsheets for those subscriptions will be created using the format of Employee Training Transactions which can be imported into SAGE as transactions. 

# Role based employee creation
- Look at creating an `AllowedJobType` table similar to `AllowedCompanyID` table. 
	- If Jobtype selected is in this table then allow the employee to be created else ignore. 
	- Need to update all Views that have 
	```sql
		INNER JOIN [Sync].[AllowedSyncCompany]   sc ON sc.SyncCompanyID = SE.CompanyID   /* Added */
	```
	to include an inner join for AllowedJobType. 
	- This will only be used to specify which Employees are added to aNS
- A different approach will be used for AutoSubscription based on RoleType
	- This can be similar to how Autosubscriptions work based on Zones. 


