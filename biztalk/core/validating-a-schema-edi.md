---
title: "Validating a Schema (EDI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6175460-2dcf-4fef-b770-02f0a058bf93
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating a Schema (EDI)
You can validate an EDI schema at design time. To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment. The validate-schema operation validates the schema based on EDI rules. You do not have to designate an input message instance to validate a schema.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To validate a schema  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project. To the project in Solution Explorer, add the message schema that you want to validate.  
  
   > [!NOTE]
   >  The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder. For information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).  
   > 
   > [!NOTE]
   >  You do not have to build the project to validate a schema.  
  
2. Right-click the schema in Solution Explorer, and then click **Validate Schema**.  
  
3. Verify that there is a message in the Output window indicating that the operation succeeded.  
  
## See Also  
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)