# SSMS/database steps for adding new client environments/report groups/report items:

- Connect to [nltintegration.database.windows.net](http://nltintegration.database.windows.net/) 
- Open the NLTADMINDB database.
>[!NOTE]
>We are simply using Camaf as the example in the below queries, please use the correct values as per the client in question. Most of the details can be retrieved from the Power-BI URL. Please get this URL from the PBI engineer(Jarrid) for the dashboard in question.

# For brand new clients:
## Add Environment

```sql
INSERT INTO [Environment].[Environment] (EnvironmentName, EnvironmentUrl,EnvironmentKey)
VALUES 	('Camaf','<https://camaf.anewspring.com/api/','xxxxxxxxxx>'));
go
```

## Add Group

- This GUID value comes from the first guid value of the power-bi report url: 
  https://app.powerbi.com/groups/3ca05449-873a-4415-ad90-0ebd62804d6f/reports/15abbaa4-9326-4329-9b10-d8333d260ac7/ReportSectionec6bd85d554e160e2412
  

```sql
INSERT INTO [PowerBI].[Group] ( GroupName, GroupBIID,EnvironmentID)
		VALUES ('CAMAF','3ca05449-873a-4415-ad90-0ebd62804d6f',13);
	go
```

## Add Report Item

- This GUID value comes from the second guid value of the power-bi report url:
    https://app.powerbi.com/groups/3ca05449-873a-4415-ad90-0ebd62804d6f/reports/15abbaa4-9326-4329-9b10-d8333d260ac7/ReportSectionec6bd85d554e160e2412
    

```sql
INSERT INTO [PowerBI].[ReportItem] (ReportItemName, ReportItemBIID,GroupID)
		VALUES  ('Camaf RPT1','15abbaa4-9326-4329-9b10-d8333d260ac7',12);
	go
```

# For existing clients:
- If the learner does not exist you will need to first add them to the Learner.Learner table.
# Add a user

```sql
INSERT INTO [TIUser].[User] (UserFirstName, UserLastName,UserEmail)
		VALUES  ('firstName','lastName','user.email.com'),
	go
```

# Linking a user to a report

```sql
INSERT INTO [TIUser].[UserReportLine] (UserID, ReportItemID)
		VALUES 
			   (57,19),
			   (58,18);
	go
```


