
- If the Client is using aNS as the LMS to be proctored we can create a DACPAC of an existing client's Proctor database to use as a template. 
	For example: 
	![[Pasted image 20240318105108.png|800]]
	![[Pasted image 20240318105216.png|800]]
	- From the DACPAC file create a new database restored from the DACPAC called `{CLIENTNAME}PROCTORDB`.
	- Next we can populate the required configuration tables:
		- aNS API keys in the `[aNewSpring].[Environment]` table.
		- Proctorio API keys in the `Proctorio.ProctorioConfig` table.
			- We can also adjust Porctorio settings column to suit client specific requirements i.e screenRecording, Audio capture, links, tabs etc refer to Proctorio API docs. 
		- Email configuration values in the `[Email].[EmailConfiguration]` table - these would be the values of the clients SMTP server if email setup is requested. 
			- Currently setup for all Proctered clients except GIFS.
		- The `LTIAdmin` table is automatically populated with any aNS user with a role greater than `Learner`.
			- In order for these Admins to become moderators they will need to be subscribed to the `Moderation/Invigulator` course on aNS
			  and then we will manually link them to their respective environment in the `Admin.ModerationEnvironmentLTIAdminLine` table.
			  - Sub-Environments can be added to `[Admin].[ModerationEnvironment]`table:
			    
			    ![[Pasted image 20240318115144.png|1000]]
---
