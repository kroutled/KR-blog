# Overview
The Proctorio reconnect functionality and the [[Exam Activity lock]] are both aNS custom plugins designed for GIFs to remove some restrictions and pain-points experienced during the proctoring of exams.

One such pain point is that learners would be disconnected(perhaps due to loadshedding or poor internet connectivity) from an assessment/exam session, and then when attempting to re-access their assessment on aNS, they would directly access the assessment activity itself, thus by-passing the previous activity which is needed to initialize the proctoring session, and authenticate the user. This means that the exam is completed on aNS directly instead of through the Proctorio wrapped version of the exam that is embedded in the app service lol, and therefore no recording/proctoring is recorded.

The core purpose of the reconnect solution is to check that the learner has not been disconnected during an assessment, and if they are it will lock the assessment activity on aNS so that when a learner goes to the exam after being disconnected they are forced to first go through the first activity once again to re-authenticate and re-initialise the proctorio session. 

# How it works
The reconnect functionality relies on an Azure Resource which is called a `Azure Relay`, the relay creates a connection between the software running on an Azure VM/server (the NLT reconnect software) and the client's Proctorio App Service. 

Some modifications need to made to the client's Proctorio App Service project for this to function correctly. 

When a learner begins an assessment they are redirected to the Proctorio App Service. The App Service has been modified to include a JS script which connects to the the NLT reconnect software running on a separate server. The script is designed to periodically send state information regarding the assessment taking place, something along the lines of: 
```js
            var liveProctorObj = {
                LearnerExternalID: "@Model.LearnerExternalID",
                CourseExternalId:  "@Model.CourseExternalId",
                ExamExternalID:    "@Model.AssessmentExternalID",
                ProctorExternalID: "@Model.ExamTagExamToProctorPartID",
                AliveCount:         0,
                StopProctor:        false,
                ProctorStatus:      "alive",
                PingMilliseconds:   "@ProctorioPlugin.BL.ProctorioReconnect.ProctorioReconnectClient.PingMilliseconds"
            }
```

The NLT reconnect software will receive this data and assess it to confirm that the learner is still connected and taking the assessment, if it does not receive the required information after the configured time frame it will then connect to aNS and lock the assessment activity for that learner, on that assessment ensuring that the learner cannot by-pass proctorio authentication and must re-authenticate before continuing. 
## Components
- App Service
- Proctor Database
- Virtual Machine 
	- Reconnect Relay
	- Relay Database

# Source code
location: [PROCTORIO_Disconnect_Server](https://dev.azure.com/NewLeafDevelopment/_git/PROCTORIO_Disconnect_Server?path=/&version=GBmaster)

# Documentation
G:/Shared drives/IT/Clients/GIFS/Project Resources/Proctorio Reconnect
