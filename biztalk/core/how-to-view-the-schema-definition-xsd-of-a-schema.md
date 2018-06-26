---
title: "How to View the Schema Definition (XSD) of a Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, viewing"
  - "managing [schemas], viewing"
  - "viewing, schema definitions"
  - "schemas, schema definition (XSD)"
  - "managing [schemas], schema definition (XSD)"
ms.assetid: 21b6d9e6-5737-4334-9fe6-15ae01f90c0d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to View the Schema Definition (XSD) of a Schema
This topic describes how to use the BizTalk Server Administration console to view the schema definition (XSD) of a schema. You might want to do this to troubleshoot schema validation errors or validate that the correct schema is deployed.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view the XSD of a schema  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to view the XSD, and then expand the application containing the schema.  
  
3. Click **Schemas**, right-click the schema, and then click **Properties**.  
  
4. In the left pane, click **Schema View**.  
  
    The XSD displays in the right pane.  
  
## See Also  
 [Managing Schemas](../core/managing-schemas.md)