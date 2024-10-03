
# Current Process

Courses:
1. Healthy Me
2. Wealthy Me 

Process: 
- 

---
## 1. Direct API

```
Description:

This would be a direct refactor of the existing Discovery integration that would make calls to the aNewSpring API as opposed to the Moodle API. 
``` 

### Pros
- Can leverage the existing Discovery integration. 
- Would not incur any additional costs. - cheapest/least amount work
### Cons
- Relies on Discovery development team which may result in longer wait times. - take longest

--- 
## 2. Moodle instance data source

```
Description:

This would work as a synchronisation where Discovery continues to use their existing integration. We would then pull data from the Moodle database and do a comparison with what is on aNewSpring and should there be any differences we can then update aNewSpring accordingly.
```
### Pros
- Less dependency on Discovery. 
### Cons
- Would incur costs to host the concurrent system. 
- May result in delayed data reflection on aNewSpring.
  
#### Custom code/middleware

---

## 3. Custom New Leaf Integration(azurefunctions.com/newLeaf/{data})

```
Description:

This would be a re-write of the integration where we receive requests from Discovery and handle the business logic of adding/updating/archiving learners, subscribing etc. ourselves.

```
### Pros
- We have more control of the integration for future updates. 
- Less reliance on the Discovery team.

### Cons
-  This would require custom development which would take time and would incur costs. 
### Phase 2
#### Standalone database 

Healthy Company
Discovery 
Individuals 
Zoho


Use webhooks on course to trigger other process that make calls to third party systems.
Worth -> integration -> aNS/Zoho/third party 

put together: for Thursday(25/07/2024)
- timelines
- costing
- requirements breakdowns(hours)