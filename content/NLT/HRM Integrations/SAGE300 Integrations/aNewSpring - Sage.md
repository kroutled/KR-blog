# Overview
This is an integration which exists between the SAGE300 People HRM system and aNewSpring as well as an [[Admin Portal]] web application that can be used to configure and manage the integration. 
The clients currently using this integration include:
- BMG
- NRCS
- Bidvest
- HSystems

---
# Process
The installation process is documented here: [[aNS-SAGE300 Integration Installation and Admin User Guide.pdf]]. 
More information regarding how the Integrator works can be found here: [[Sage300 Integration database and views explained]]

---
## Setting up Linked Servers

This step is in the case that the SAGE application and SAGE DB are hosted on a different server to the server that is hosting the NLT Integrator software and Integration database. 
See below images as a reference which show the configured linked server for HSystems. In this case we had two servers:
1. NLT-SRV -> Which hosted the Integration database and Integration Software.
2. NLT-SAGE -> Which hosted SAGE300 and the SAGE DB.
Below we created a linked server on the NLT-SRV server which connected to the NLT-SAGE server so that we would be able to pull the NLT SAGE views into the integration database. 

![[HRM Integrations/SAGE300 Integrations/Assets/image.png|800]]

![[HRM Integrations/SAGE300 Integrations/Assets/image (1).png|800]]

![[image (2).png|800]]

>[!Note]
>The above documentation and process is subject to change in the future as the SAGE API is now available and will achieve the integration more effectively. 

---
