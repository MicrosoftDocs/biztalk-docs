---
description: "Learn more about: User Rights for Managing TPE"
title: "User Rights for Managing TPE"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# User Rights for Managing TPE
Solution developers, system administrators, or IT/Operations personnel must have administrative rights to retrieve or deploy the tracking profile into a database associated with an assembly.  
  
> [!IMPORTANT]
>  You cannot define user roles or grant or deny user permissions using Tracking Profile Editor (TPE). You can only define these user roles and associated permissions in Microsoft SQL Server.  
  
 With TPE, administrators can:  
  
-   Retrieve an active tracking profile associated with one or more assemblies from the BizTalk Management database  
  
-   Modify the tracking profile  
  
-   Apply a new or modified tracking profile into the BizTalk Management database  
  
-   Modify saved tracking profile files (.btt)  
  
    > [!NOTE]
    >  Tracking profile files are not the final authority on the contents of a profile. TPE can save a profile to a file, although it primarily pulls from and publishes the profile contents to the BizTalk Server and BAM databases. Tracking profile files can still be used to edit or update the stored profile as long as the file contents match the information stored in the databases. In addition, tracking profile files can be packaged within a BizTalk Server application package. Application packages that include tracking profile files automatically invoke BTTDeploy.exe to apply the tracking profile when the MSI package is imported to a given BizTalk Server installation.  
  
> [!IMPORTANT]
>  In the TPE workflow, assuming the development and deployment tasks are separated, as is typically the case, the person responsible for deployment should have read-only access to the .btt file and the associated assembly file.  
  
## See Also  
 [BAM Workflow](../core/bam-workflow.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)
