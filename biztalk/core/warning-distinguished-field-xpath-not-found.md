---
title: "Warning - Distinguished Field XPath Not Found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.distingFieldXPathNotFound"
ms.assetid: a925c39c-9ae1-4334-b329-aa2f5afd97ce
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Warning - Distinguished Field XPath Not Found
**Error Code**  
  
 BEC1006  
  
 **Explanation**  
  
 The node corresponding to the indicated Distinguished Field promotion may not exist in the schema. BizTalk Editor cannot resolve complex XPath specifications, and if you edited the promoted property XPath in the **Edit Instance XPath** dialog box, it may or may not correctly identify the node you intended to promote.  
  
 **User Action**  
  
 You can keep this warning from appearing by changing the XPath for the promoted property in the **Edit Instance XPath** dialog box, which you can access from cells in the **Node Path** column of the table on the **Distinguished Fields** tab in the **Promote Properties** dialog box. You can access the **Promote Properties** dialog box from the **Promote Properties** property of the **Schema** node in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.