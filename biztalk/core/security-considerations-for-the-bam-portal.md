---
description: "Learn more about: Security Considerations for the BAM Portal"
title: "Security Considerations for the BAM Portal"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security Considerations for the BAM Portal
Using the principle of least privilege, user accounts should have restrictive permissions to perform routine tasks in the BAM portal. Keep the following points in mind as you set up your user accounts for BAM to balance security with appropriate access for users.  
  
## User accounts  
 User accounts with minimum permissions are not able to use the BAM portal distributed navigationfeature. To be able to use this feature, these accounts must have sufficient permissions to allow access to the Web services on the remote computer as well as on the local computer.  
  
 User accounts for the BAM Web services must have permissions to access all referenced databases and must be a member of the BAM_ManagementWS role in the referenced databases.  
  
 For the following user types, you should be aware of these considerations:  
  
-   Domain Users, must have access permissions on remote computers that host Primary Import databases that are being accessed.  
  
-   Users who are assigned Local User role, cannot use distributed navigation.  
  
## Administrator accounts  
 Administrators must be members of the securityadmin or sysadmin groups to grant permissions to domain users.  
  
 To run the BAM Management utility, you must be at least a database operator for the BAM databases.  
  
## See Also  
 [BAM Portal](../core/bam-portal.md)
