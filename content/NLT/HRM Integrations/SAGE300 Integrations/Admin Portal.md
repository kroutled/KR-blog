This is a web application that is hosted on IIS on the same Server as the Integration database and can be used for further configuring and managing of 
the [[aNewSpring - Sage]] and [[Efront - Sage]] Integrations and how data is synchronised between the two systems.

This would include things such as: 
- field mappings
	- Course status' on aNS and SAGE.
- Criteria to be met for subscribing employees to specific courses.

It looks like this: 
![[Pasted image 20240319121445.png|1200]]


## Course List
- Status Column of `Registers` or `Not Yet Registered` refers to if there is a corresponding Course on aNS with an External ID that matches the Training Dictionary Code -> This would be done manually(taking the training dictionary code and adding as external ID on the course on aNS) - this would then cause the course to reflect as `Registered` on the next synchronisation cycle.
- Click `View` to select particular course. 
	- We can then set configurations for this course using the tabs on the right hand side of the screen as explained below. 
---
## Basics Tab 
#### Details box - Course details
![[Pasted image 20240319131749.png|1200]]

#### Criteria box - used to set subscription criteria.

The below screenshot contains: 
- The course auto-subscription settings. These are criteria that determine how employees are automatically subscribed to courses on aNS.
	1. `Auto Subscribe New Employees on creation` checkbox - selecting this checkbox will activate/deactivate the automatic subscription process for the selected course when satisfying the below criteria.
	2. `All New Employees`/`Specific New Employees` radio buttons - selecting the `All New Employees` option will allow all employees on the SAGE system to be auto-subscribed to courses based on if they've met the described criteria. 
	   ![[Pasted image 20240319143031.png]]
	   
	   The `Specific New Employees` option in this case allows us to specify from which Zones an employee must be from to be auto-subscribed to the selected course.
	   This can be edited in the source code to account for other possible criteria. I.E. the role of the employee instead of the zone, provided the data is retrievable from SAGE Views and within SAGE itself. 
	   ![[Pasted image 20240319143127.png]]
	
	3. `Only Subscribe after...` checkbox - Will give us an option called `Click to manage the 'Subscribe after' settings on this Course.` which produces a popup.
		In this pop up we can add a list of one or more intervention courses. These are other courses the learner would need to be subscribed to and have achieved the specified status(intervention result) on before being subscribed to the selected course.
	   . 
![[Pasted image 20240319132213.png|1200]]

Below is the view of the intervention popup. Here we can:
- Select the intervention course we would like to include and click the `Add` button. 
- The intervention course is added to the pane on the right. 
- We can click `Edit` and scroll down to the bottom of the page to edit the required `Intervention Result` needed on that intervention course for the criteria of autosubscribing the employee to the selected course. 
![[Pasted image 20240319132250.png|1200]]
 When we edit these courses we can further configure the criteria by setting what status the dependant courses need
to have in order to meet the criteria of subscription as well as a duration of when this should happen.
For example: 
- We add the COMPETENT code to the intervention result list(`Selected Intervention List`)
- We then select the condition which specifies at what time after achieving the specified Intervention result will the auto subscription subscribe the employee to the selected course.
	- Here we have the options of:
		1. Immediately -> This is as soon as the next sync loop runs the employee will be subscribed to the selected course.
		2. After the specified month period -> This will be after the `Period(Month)` time has elapsed after achieving the Intervention Result on the Intervention course.
		3. On specific date -> On the date specified the the employee will be subscribed to the selected course if having achieved the Intervention Result on the Intervention course.
		4. Not yet selected -> Does not take the Intervention Course into account as required to subscribe to the selected course, thus the employee will not be auto-subscribed until the condition is set to one of the above. 
![[Pasted image 20240319132714.png|1200 ]]

>[!Note]
>When removing these intervention courses you will first need to remove the Intervention Result mapping by hitting Edit, scrolling down and clicking the white 'X' on the Intervention Result. Then you should be able to remove the Intervention Course from the `##### Selected AfterCourse List` by selecting the `Delete` button. 
>
>If an Intervention Course contains a mapping condition it will throw an error. 
>
>![[Pasted image 20240320150957.png|800]]
>![[Pasted image 20240320151046.png|800]]
#### Subscription Default Values box 

When we create or update subscriptions on aNS the synchronisation will generate an excel spreadsheet that can be imported as a `System Defined Batch` - `Employee Training Transactions` batch as per the Utilities functionality on SAGE. 
![[Pasted image 20240320133019.png|1200]]
- Select `Process` in the top left corner of screen:
  ![[Pasted image 20240320133133.png|800]]
  Select the company and the Batch option:
  ![[Pasted image 20240320133224.png|800]]
  From here we can select the .xlsx file from the share folder that is setup: 
  ![[Pasted image 20240320133341.png|800]]

This `Subscription Default Values box ` section is used to specify properties to include in the batch excel spreadsheets generated, that correspond to Properties of the `Employee Training Transaction` that are not  inherently apart of aNS so that the transactions imported contain the correct SAGE specific information. 

![[Pasted image 20240320132648.png|800]]

---
## Subscription Tab

This is a list of subscriptions/employee training transactions associated to the selected course. 

![[Pasted image 20240320141906.png]]

---
## Activities Tab
>[!Note]
>This is the same functionality as the [[Final Activities Extension]] 


---
## Interventions Tab
Under the interventions tab is where we can map which  course status is mapped to which SAGE Training Dictionary `Intervention Result`: 
![[Pasted image 20240319140711.png|1200]]

---

# Control Page

## Intervention Results
The Control page is where we configure and map the global `Intervention Results` for subscriptions. These are the values that will be defaulted to if the `Intervention Results` are not mapped on the Interventions Tab of the Course page. 

To create new Intervention Results(Status') on SAGE we can:
- Navigate to the Parameters tab -> Expand all -> Search 'Intervention Results' -> select Intervention Result. 
- Add a new entry. This entry will represent/correspond to the Subscription Status' as they are on aNS. 
	![[Pasted image 20240320143714.png|800]]

Add the following:
- Not Yet Registered On ANS
- Registered On ANS
- Not Yet Started On ANS
- In-Progress On ANS
- Completion Passed On ANS
- Completion Failed On ANS
  
We also add a record for Reason for failure under the  Parameters tab -> Expand all -> Search 'Intervention Reason' -> select Intervention Reason tab. 
- Reason for Failure
![[Pasted image 20240320145222.png|800]]

From here we can then map to these SAGE Intervention results on the Control Page as such: 
![[Pasted image 20240320145439.png|800]]

## Subscription List
This section will display a list of all subscriptions/Employee Training Transactions
![[Pasted image 20240320145916.png|1200]]

## Course After Course Subscription List
This section will display a list of subscriptions added to aNewSpring as part of the auto-subscription functionality on the Course Page. 

It describes the following:
- Action: 
- Course:  This is the name of the Course that the employee was automatically subscribed to on aNewSpring.
- After Course: This is the name of the Intervention Course that was set as a pre-requisite to the auto-subscription of the employee to the course.
- Employee: This is the name of the employee who has been automatically subscribed. 
- Registration Date: This is the date that the pre-requisite Intervention conditions were met.
- Processed Date: This is the date that the Course was subscribed to automatically based on conditions set on the Intervention level(Immediately, number of months, specific date etc.)
![[Pasted image 20240320151634.png]]