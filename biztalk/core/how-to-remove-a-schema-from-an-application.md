---
title: "How to Remove a Schema from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, schemas"
  - "applications, schemas"
  - "schemas, deleting"
  - "managing [schemas], deleting"
  - "managing [schemas], applications"
  - "schemas, applications"
ms.assetid: 17dd5869-b56c-4166-9f02-03e04e691eda
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Schema from an Application
This topic describes how to use the BizTalk Server Administration console to remove a schema from an application. This procedure removes the schema from the BizTalk Management database for the group as well. You might want to remove a schema after deploying a new version of the schema. For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).  
  
 When you remove a schema, and a previous version of the schema having the same root namespace exists in the application, the previous version will become active.  
  
 When you remove a schema, the following occurs:  
  
-   The schema is deleted from the BizTalk Management database.  
  
-   The BizTalk assembly that contains the schema is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.  
  
-   As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a schema  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema to remove and the application containing the schema.  
  
3. Click **Schemas**, right-click the schema, and then click **Remove**.  
  
## See Also  
 [Managing Schemas](../core/managing-schemas.md)