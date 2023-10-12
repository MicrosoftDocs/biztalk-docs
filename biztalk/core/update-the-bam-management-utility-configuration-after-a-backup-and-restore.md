---
description: "Learn more about: How to Update the BAM Management Utility Configuration After a Backup and Restore"
title: "How to Update the BAM Management Utility Configuration After a Backup and Restore"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Update the BAM Management Utility Configuration After a Backup and Restore
When the server\database name combination changes as the result of a change in your BizTalk Server environment such as a backup and restore sequence, you must update the BAM management utility configuration file (bm.exe.config) to reflect these name changes.  
  
### To update the BAM management configuration file a after backup and restore  
  
1. Open the bm.exe.config file using Notepad by clicking **Start**, clicking **Run**, typing notepad c:[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\bm.exe.config, and then clicking **OK**.  
  
2. Locate the appSettings section in the file and change the following values:  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="oldServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
3. to  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="newServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
4. Save the file.  
  
## See Also  
 [Managing BAM Databases](../core/managing-bam-databases.md)
