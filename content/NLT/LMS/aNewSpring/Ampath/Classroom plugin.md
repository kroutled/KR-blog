![[Pasted image 20240417131607.png]]

- searchable fields
- drop downs come from a spreadsheet: 

TODOs: 
- Update Trins POC to include all the things from the spreadsheet Prisella shared.
- Its basically a way to add and manager learners.
- Capture on the job training - Learner/Course/Duration see above screenshot.
- Needs drop downs that are search able and has all training from spreadsheets.
	- Should contain aNS courses as well. 



Add remaining bindings for 
- TrainingCriteriaDetailsID,	
- TrainingTypeID,	
- TrainerName,	
- Venue,	
- LearnerName,	
- JobTitle,	
- Duration,	
- Compotent,	
- ToFromDate
Add CRUD operations for:
- TrainingLog records
- Disciplines
- Topics
- TrainingOutcomes
- TrainingCriteria
- TrainingTypes
- etc
Add PDF/xlsm functionality to Training Logs table and per record. 
Add search functionality for Training Logs.
Add aNS API functionality to pull Learner data. (Keep in mind that this will change in future to pull employee info from SAGE).