---
description: "Learn more about: Restoring Databases Not Included in the Backup BizTalk Server Job"
title: "Restoring Databases Not Included in the Backup BizTalk Server Job"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Restoring Databases Not Included in the Backup BizTalk Server Job
This section describes how to restore databases that are part of the overall BizTalk solution but are not backed up by the Backup BizTalk Server job. All databases that are part of a BizTalk solution will be backed up by using the Backup BizTalk Server job except for the following:  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases  
  
- BAM databases when BAM is enabled and configured using BM.exe  
  
  This section also describes how to update database references after restoring the databases listed above and includes information about resolving incomplete BAM activity instances.  
  
## In This Section  
  
-   [Restoring Analysis Services and Supporting Databases](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [Updating Database References](../technical-guides/updating-database-references.md)  
  
-   [How to Resolve Incomplete BAM Activity Instances](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)
