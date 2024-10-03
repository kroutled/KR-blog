Often times we will receive a query to add a prior acknowledgement for Wellness Warehouse. This is so that Learner's who have completed class room based Courses or Courses offered on aNewSpring but not completed on aNewSpring may be accounted for on the TIS. 

Generally these requests will come from Abby or NLT IT support as such: "please give acknowledgement for [Goqoayanda@wellness.co.za](mailto:Goqoayanda@wellness.co.za) on this course CRSCUSEXPKZN". 
In order to complete this request we will need the email address of the Learner and the CourseExternalID.

On the WELLNESSWAREHOUSEDB database located here: sqls-wellness-prod.database.windows.net there is a table called [Subscription].[SubscriptionHistoric] where these records are stored. 

>[!Note]
>We use a negative ID for these records to identify them on Power Bi 

The Insert_Historic_Data.sql script to account for all prior acknowledged records can be found here on the Google Drive: 
G:\Shared drives\IT\Clients\WellnessWarehouse\Training Intelligence\Database

Otherwise the following process may be followed:
1. Open the [Subscription].[SubscriptionHistoric] table and run the following to see the latest ID: 
```sql
SELECT *
FROM [Subscription].[SubscriptionHistoric]
order by [SubscriptionId] asc 
```
2. Check the [Learner].[Learner] table to confirm the learner exists using their email/login:
```sql
SELECT *
FROM [Learner].[Learner]
WHERE LearnerEmail = 'Goqoayanda@wellness.co.za'
```
3. Check the [Course].[Course] table to confirm the course exists using the CourseExternalID:
```sql
SELECT *
FROM [Course].[Course]
WHERE CourseExternalID = 'CRSCUSEXPKZN'
```
4. Once confirmed that both the learner and the course exist we can run the following to add the historic record:
```sql
INSERT INTO [Subscription].[SubscriptionHistoric] ( SubscriptionId,LearnerLogin,CourseExternalId) 
VALUES 
(-676, 'Goqoayanda@wellness.co.za', 'CRSCUSEXPKZN')
GO
```
5. Finally we run the following to update all records in the [Subscription].[SubscriptionHistoric] table to have the static data used on the other columns:
```sql 
Update [Subscription].[SubscriptionHistoric]
set SubscriptionActive        = 1, 
	SubscriptionCompleted     = 1,
	SubscriptionCompleteDate  = '2023-09-1',
	SubscriptionSubscribeDate ='2023-08-1',
	SubscriptionStartDate     ='2023-08-1',
	SubscriptionGradeDate     ='2023-09-1',
	SubscriptionParts         ='[]'
```

>[!Note]
>It's important to append the code at step 4 to the Insert_Historic_Data.sql script and save the file, as this is our backup of all historic subscriptions added to the DB.
