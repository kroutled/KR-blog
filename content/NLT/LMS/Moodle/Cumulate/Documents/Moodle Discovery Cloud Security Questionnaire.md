
### Introduction 
**1.1 Who is the cloud provider whose services are being requested?**
```
Moodle Learner Experience platform hosted on Amazon Web Services(AWS).
```

**1.2 Please confirm that an NDA is in place with this provider to ensure integrity and confidentiality of data**
```
Yes.
```

### Cloud Security Questions

**2.1 Where is data geographically stored/located for your service?**
```
Africa(Cape Town).
```

**2.2 What is the data retention policy applied to your service?**
```
On termination of the user agreement, New Leaf Technologies shall provide the company with a copy of the processed personal data in a customary format for electronic processing on request, in compliance with the Service Level Agreement. New Leaf Technologies shall not make any claim to this copy. Personal data will in any event be irreversibly destroyed 90 days after the termination.
```

**2.3 What is the backup policy applied to data store within your service?**
```
Backups (in the form of snapshots) of the production environment are made on a weekly basis. The backups are retained for 90 days.
```

**2.4 Is backup data encrypted at rest? If so, please also include information as to what standards are adhered to in this space.**
```
Yes, Amazon EBS encryption uses AWS KMS keys when creating encrypted volumes and snapshots.
```

**2.5 Do you have a formal security policy? If so, please include this documentation**
```
Yes, please see #Security and compliance pdf from AWS/ https://docs.aws.amazon.com/whitepapers/latest/aws-overview/security-and-compliance.html.
```

**2.6 Do you support encryption in transit to ensure that all data between Discovery and yourselves is kept secure?**
```
Encrypted connection : All environments are configured on AWS to only be accessed through an HTTPS connection. This makes it impossible for third parties to intercept information that is transmitted through this connection. By default we ensure all environments are set to automatically redirect HTTP requests to HTTPS.
```

**2.7 Are your systems audited by third parties on an annual basis to ensure compliance with security policies?**
```
At New Leaf Technologies, our Moodle website is hosted on Amazon Web Services (AWS), which adheres to stringent security standards and undergoes regular third-party audits to ensure compliance with industry-leading security policies. AWS provides comprehensive security measures and compliance certifications, which include but are not limited to SOC (System and Organization Controls) 1, 2, and 3, ISO 27001, and PCI DSS (Payment Card Industry Data Security Standard).

While we do not conduct independent third-party penetration tests on the Moodle Learning Experience Platform (LXP) itself on a routine basis, we rely on AWS's robust security infrastructure. Additionally, we are committed to conducting third-party penetration tests on the Moodle LXP upon client request to ensure it meets specific security requirements and compliance standards.
```

**2.8 Do you keep a full audit trail of who accesses data?**
```
At the time of writing, full audit trail functionality for tracking who accesses data has not been activated, as we have taken over an existing system. However, this feature can be enabled upon request and will be available at an additional cost.
```

**2.9 If your product links to Discovery’s Active Directory for authentication, do you support two factor authentication?**
```
We do not access Discovery’s Active Directory and only provide/support for SSO as per Discovery's specifications. 
```

**2.10 Does your service provide high availability and/or redundancy?**
```
While the t3.large EC2 instance itself does not have built-in redundancy, our service can provide high availability and redundancy through additional configurations such as Auto Scaling groups, Elastic Load Balancers, and multi-AZ deployments. These features can be set up upon request to ensure reliable and redundant operations.
```

**2.11 What security standards and/or frameworks does your organization adhere to?**
```
AWS maintains compliance with a wide range of certifications and frameworks, including but not limited to:  

- SOC (System and Organization Controls) 1, 2, and 3
- ISO/IEC 27001
- PCI DSS (Payment Card Industry Data Security Standard)
- HIPAA (Health Insurance Portability and Accountability Act)
- GDPR (General Data Protection Regulation)

Please see shared security document.
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
While we do not conduct independent third-party penetration tests on the Moodle Learning Experience Platform (LXP) itself on a routine basis, we rely on AWS's robust security infrastructure. Additionally, we are committed to conducting third-party penetration tests on the Moodle LXP upon client request to ensure it meets specific security requirements and compliance standards.
 
```

**2.15 How is Discovery data segregated from other customer data?**
```
Currently Discovery data is not segregated from other customer data but does adhere to proper security standards and practices. 
```

**2.16 Is data protected between end-points, or only up to the company perimeter?**
```
Internal traffic (between end-points) is protected by the AWS VPC (Virtual Private Cloud).
```