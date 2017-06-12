---
title: "How to Determine and Set Event Writer Roles for Activities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73bfe8ff-167a-4bf0-ab87-3926290d52d8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Determine and Set Event Writer Roles for Activities
BAM provides two modes of security when writing events on activities. You can grant permissions to write events on individual activities or you can grant permissions to write events on all deployed activities.  
  
 Activity-level security is provided by activity event writer roles that are created when you deploy a BAM definition. For example, if you deploy a definition for an activity named CreditCard, BAM creates an event writer role named bam_CreditCard_EventWriter. This role has permissions to write events for the activity. To grant a user permissions to write events for the activity, you add the user to the role.  
  
 Alternatively, you can grant users rights to write eve2nts to all activities by adding them to the super role BAM_EVENT_WRITER, which has permissions to write to all activities.  
  
## Prerequisites  
 To perform this procedure, you must have the following:  
  
-   A connection to BAMPrimaryImportDb on which the activity is deployed.  
  
-   DBO permissions on the database.  
  
### To add a user to an event writer role  
  
1.  Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.  
  
3.  In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.  
  
4.  Click the **New Query** icon on the toolbar.  
  
5.  Copy the following commands and paste them into the Query Window. Replace the domain name, user name, and activity name placeholders with the appropriate values.  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'bam_<activity name>_EventWriter', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  Role names are case-sensitive. Activity names are also case-sensitive, that is, they must match the case used when deploying the activity.  
  
6.  Click the **Execute** icon on the toolbar or press F5 to run the commands.  
  
### To add a user to an event writer super role  
  
1.  Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to SQL Server** dialog box, select the SQL Server and the appropriate authentication method, and then click **Connect**.  
  
3.  In the **Object Explorer** pane expand **Databases**, and then select the BAM Primary Import database.  
  
4.  Click the **New Query** icon on the toolbar.  
  
5.  Copy the following commands and paste them into the Query Window. Replace the domain name and user name with the appropriate values.  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'BAM_EVENT_WRITER', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  Role names are case sensitive. You must specify the event writer role as specified.  
  
6.  Click the **Execute** icon on the toolbar or press F5 to run the commands.  
  
## See Also  
 [Managing BAM Security](../core/managing-bam-security.md)