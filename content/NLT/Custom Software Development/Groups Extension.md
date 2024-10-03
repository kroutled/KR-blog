# Purpose

On TIS with regards to groups and group information we would like to see:
- Learners associated to the group. 
- Courses associated to the group.

On aNS with regards to groups and group information there is no way to pull a list of groups directly from the API(/groups) which is needed for the TIS, therefore we have a Groups extension that is used to manually capture this information and store to the clients TIS DB so that it may be pulled into their TIS dashboard. 
- This way we can get a list of all groups directly from the database. 

# Features
- Add/Edit Groups(Should be an exact replication of the corresponding group on aNS).
- Add/Remove corresponding courses to/from the above mentioned groups as reflected on aNS.
  
>[!Note]
>This is all a manual process that needs to be administered by the client in order for it to reflect correctly on TIS

# Process
- Admin uses the extension to create replica of Group on aNS with externalID and other data, this is added to the Groups table in their TIS DB. 
- Admin then adds corresponding Courses via the extension and the extension will link the Courses to the Groups in the Group.GroupCourseLine. 
- The extension then uses the Group ExternalID from the database Group to make a call to the aNS API([/getGroupUsers/{groupID}](https://wellnesswarehouse.anewspring.com/apidocs#!/groups/getGroupUsers)) using the group externalID to retrieve a list of all users associated to that Group and inserts those users into the Group.GroupLearnerLine table.
- Thus we can see all information of courses and learners that are related to Groups when filtering by groups on the TIS dashboard.  



# Project Location
- https://dev.azure.com/NewLeafDevelopment/_git/NLT%20ANS%20Extension?path=/NLT_ANS_Extension

- You may note on this project that there are a few DataAccess{clientName} projects, this is a newer convention to keep the data connections for the various clients using this extension in a more organised format and to prevent confusion and conflicts as the number of clients increases.