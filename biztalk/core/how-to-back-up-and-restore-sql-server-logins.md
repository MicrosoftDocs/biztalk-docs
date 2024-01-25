---
description: "Learn more about: How to Back Up and Restore SQL Server Logins"
title: "How to Back Up and Restore SQL Server Logins"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Back Up and Restore SQL Server Logins
Back up and restore SQL Server logins associated with BizTalk Server.  
  
## BizTalk Server SQL Server Security Logins  
 The SQL Server security logins listed below are associated with BizTalk Server. You may have additional logins associated with the BizTalk Server applications you have created. You need to back up the logins and restore them when moving the BizTalk Server databases to a new server or new instance of SQL Server.  
  
-   BizTalk Application Users  
  
-   BizTalk Isolated Host Users  
  
-   BizTalk Server Administrators  
  
-   BizTalk Server Operators  
  
-   SSO Administrators  

## Prerequisites  
You must be a member of the **Administrators** security role on the SQL Server where you backup and restore the logins.  
  
## Back up a login using a script  
  
1.  Open **SQL Server Management Studio**.  
  
2.  Expand **Security**, and expand the list of **Logins**.  
  
3.  Right-click the login you want to create a backup script for, and then select **Script Login as**.  
  
4.  Select **CREATE To**, and then select one of **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script. Typically, the destination is a file with a **.sql** extension.  
  
5.  Repeat this procedure from Step 3 for each login you want to script. Refer to the list of BizTalk Server related logins to determine which logins you need to script.  
  
## Restore a login from a script  
  
1.  Open **SQL Server Management Studio**.  
  
2.  On the **File** menu, **Open** the file containing the scripted login.  
  
3.  Execute the script to create the login.
