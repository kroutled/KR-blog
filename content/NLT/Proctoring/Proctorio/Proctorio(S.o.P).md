# **Overview:** 
Proctorio is a cutting-edge proctoring tool specifically crafted to address the challenges of conducting secure online exams and assessments within a Learning Management System. With a focus on maintaining academic integrity, this solution provides a comprehensive set of features that empower educational institutions and instructors to confidently deliver and assess exams in virtual environments.

Please view the [[Proctorio Overview.pdf]] document for further explanation and useful diagrams.
There is also a short demo of the learner and moderator processes which can be found here [[Proctoring Process]].
## **Process**
- 3 activities
	- Authentication 
	- The Assessment
	- Moderation 
- This order is important. 
  
- The user clicks the Authentication button, this is an external activity that sends an LTI request to the clients Proctorio App Service. 
- The app service will then forward the learner to a Proctorio link for authentication using the Proctorio API. 
- Next up the App Service will take the LTI request and use this to generate an SSO token for the user using the aNS API, set the redirection URL to the next activity(Assessment) and request the Proctorio urls from the Proctorio API. Finally it will redirect the learner to the Assessment in aNS which is now embedded and wrapped in the App Service and can be successfully Proctored. 
## **Diagrams**

Basic architectural overview of the Proctoring solution:
![[Pasted image 20240319124447.png|800]]

User flow and corresponding course/activity structures for Proctoring setup:
![[Pasted image 20240319124620.png|800]]
## **Proctorio Setup**
To setup an end to end T.I.S solution for a client follow the following steps:

>[!Note]
>The aNewSpring environment will need to exist first before following the below steps.

1. [[Environment setup]]
2. [[Database setup]]
3. [[Project setup]]
4. [[Course setup]]

---
