# Overview
A revised CPD(Continuous Professional Development) policy was released effective 1 January 2020. This policy moved the measurement of lifelong learning, for the purpose of professional body reporting, from input (hours) to output (competence relevant to your role).

Basically practicing professionals need to attain a certain number of hours annually in order to stay up to date and compliant in their professions.

GIFs offers courses which contribute to these hours of continuous learning needed by SAICA(Regulatory body)

The purpose of this software is to generate a PDF report that summarises the hours accumulated during the progression of a learner through a course's activities. 

Each Activity is worth 2 hours and courses are sold as bundles of 6, 8, 12, 18 and 22 hours. 

# Technical overview
An External Activity(the one that sends an [[LTI]] request when selected) is added to the end of the courses that are used to track for CPD compliance. This external activity sends an LTI request which contains the learner's info and the course info. This info can be used to make API calls to get the course parts of the course for that learner which can then be used to work out the number of hours per completed part(activity) of the course and then generate an individual pdf document that certifies that the learner has accumulated those hours. 

Example on Production:
[https://outsurancestatementofhours.azurewebsites.net/](https://outsurancestatementofhours.azurewebsites.net/)

# Deployment
1. Create an App service on Azure. 
2. Pull the code from: https://dev.azure.com/NewLeafDevelopment/NLT_Statement_Of_Hours.
3. Create a new branch for the new client.
4. Update code:
	1. Change Connection String to point to correct client environment. 
	2. Update C.I images/assets in PDF template.
5. Push new branch to Devops.
6. Publish the project to newly created App Service.
![[Pasted image 20240311130504.png|800]]
# aNewSpring Setup

1. Go to the Template of the course you would like to use the Statement of Hours extension for. 
2. Add a new block with a name such as 'Cumulative Statement of Hours'.
![[Pasted image 20240311124058.png|800]]
3. On the 'Cumulative Statement of Hours' block, click the '+ ACTIVITY' button.
4. Scroll down and select the External activity (LTI) option under 'OTHER', click 'CREATE AND EDIT'
![[Pasted image 20240311124257.png|800]]
5. Name the Activity 'Statement of Hours' and set the 'Link (including http(s)://)' field to equal the URI of the App Service created to host the extension described above.
![[Pasted image 20240311124602.png|800]]
6. Save.
7. On the course there will now be an activity that when click will generate the Statement of Hours PDF for that Learner. 
![[Pasted image 20240311125009.png|800]]
![[Pasted image 20240311125033.png|800]]

>[!Note]
>Further documentation can be found on the Google drive at:
>G:\Shared drives\IT\Clients\GIFS