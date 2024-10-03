
### Introduction 
**1.1 Who is the cloud provider whose services are being requested?**
```
aNewSpring Learner Experience platform hosted by Amazon Web Services.
```

**1.2 Please confirm that an NDA is in place with this provider to ensure integrity and confidentiality of data**
```
Yes.
```

### Cloud Security Questions

**2.1 Where is data geographically stored/located for your service?**
```
Ireland.
```

**2.2 What is the data retention policy applied to your service?**
```
On termination of the user agreement, aNewSpring shall provide the company with a copy of the processed personal data in a customary format for electronic processing on request, in compliance with the Service Level Agreement. aNewSpring shall not make any claim to this copy. Personal data will in any event be irreversibly destroyed 30 days after the termination.
```

**2.3 What is the backup policy applied to data store within your service?**
```
Backups (in the form of snapshots) of the production environment are made on a daily basis. The backups are retained for 30 days.
```

**2.4 Is backup data encrypted at rest? If so, please also include information as to what standards are adhered to in this space.**
```
Backup data is indeed encrypted at rest, using the AES-256 standard.
```

**2.5 Do you have a formal security policy? If so, please include this documentation**
```
Yes. See attached Security ENv1.4.pdf.
```

**2.6 Do you support encryption in transit to ensure that all data between Discovery and yourselves is kept secure?**
```
Encrypted connection : All environments with an [anewspring.nl](http://anewspring.nl/) or [anewspring.com](http://anewspring.com/) subdomain can be accessed through an HTTPS connection. This makes it impossible for third parties to intercept information that is transmitted through this connection. Optionally, an environment can be set to automatically redirect HTTP requests to HTTPS. This is enabled by default for all environments created after 21 October 2015. For customer specific domains, an SSL certificate can be installed against payment.
```

**2.7 Are your systems audited by third parties on an annual basis to ensure compliance with security policies?**
```
aNewSpring is ISO 27001 certified. See attached - A New Spring B.V. ISO Certificate 2022-2025 (EN).

A pentest on the aNewSpring platform is performed by a specialised company on a yearly basis to verify that the measures that have been taken to prevent vulnerabilities are (still) effective. The latest report is available upon request.
```

**2.8 Do you keep a full audit trail of who accesses data?**
```
All requests made to the web application are logged, including who was logged in at the time. However, exactly what data was accessed during that request isn't explicitly logged (e.g. when an administrator views the user list, not all users that are in the list are logged, only the fact that the user list was requested). Furthermore, important operations (e.g. deletions) on important objects (e.g. users, courses) are logged to an audit log.
```

**2.9 If your product links to Discovery’s Active Directory for authentication, do you support two factor authentication?**
```
Yes we do support 2 factor authentication.
```

**2.10 Does your service provide high availability and/or redundancy?**
```
aNewSpring guarantees a standard average minimum Availability of 99% per month during and outside office hours.

aNewSpring strives to minimise data loss from the database on the server in case of an emergency for the web application. It does this by using a back-up database in a redundant environment that is continuously synchronised with the web application's current database. Data that is removed by a user action (intentionally or otherwise) falls outside of the regulation regarding data loss.

Please see attached detailed SLA - Service Level Agreement (SLA) aNewSpring ENGv7.
```

**2.11 What security standards and/or frameworks does your organization adhere to?**
```
The system is ISO 27001 certified - See attached certificate - A New Spring B.V. ISO Certificate 2022-2025 (EN).

During the development of the learning platform, high priority is given to preventing the vulnerabilities from the OWASP Top 10 ([https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)). Measures have been taken against the majority of these vulnerabilities. For vulnerabilities for which no (complete) measures have been taken, an plan of action has been drawn up to implement them as soon as possible. Upon request, a list will be provided listing the current state of affairs regarding the measures that have been taken.

Pentests

A pentest on the aNewSpring platform is performed by a specialised company on a yearly basis to verify that the measures that have been taken to prevent vulnerabilities are (still) effective. The latest report is available upon request.
```

**2.12 What legislative requirements does your service currently adhere to?**
```
GDPR.
```

**2.13 Do you have a data destruction policy? If so, please provide information surrounding how data is destroyed.**
```
During the contract with the customer, no data is deleted automatically. When the contract is terminated, the customer database is deleted. After the retention period of the backups, the customer data is definitively deleted/destroyed.
```

**2.14 Have your services been subjected to a penetration test conducted by a third party in the past 12 months?**
```
See the attached report external penetration test aNewSpring LMS 20231115.pdf and its addendum.

- Report External Penetration Test aNewSpring LMS 20231115.
- Report External Penetration Test aNewSpring LMS 20231115 - addendum.
```

**2.15 How is Discovery data segregated from other customer data?**
```
Every learning environment uses a separate database.
```

**2.16 Is data protected between end-points, or only up to the company perimeter?**
```
Internal traffic (between end-points) is protected by the AWS VPC (Virtual Private Cloud).
```