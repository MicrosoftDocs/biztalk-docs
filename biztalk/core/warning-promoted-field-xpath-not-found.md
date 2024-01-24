---
description: "Learn more about: Warning - Promoted Field XPath Not Found"
title: "Warning - Promoted Field XPath Not Found"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.promoFieldXPathNotFound"
---
# Warning - Promoted Field XPath Not Found
**Error Code**  
  
 BEC1005  
  
 **Explanation**  
  
 The node corresponding to the indicated property field promotion may not exist in the schema. BizTalk Editor cannot resolve complex XPath specifications, and if you edited the promoted property XPath in the **Edit Instance XPath** dialog box, it may or may not correctly identify the node you intended to promote.  
  
 **User Action**  
  
 You can keep this warning from appearing by changing the XPath for the promoted property in the **Edit Instance XPath** dialog box, which you can access from cells in the **Node Path** column of the **Property Field List** table on the **Property Fields** tab in the **Promote Properties** dialog box. You can access the **Promote Properties** dialog box from the **Promote Properties** property of the **Schema** node in the Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.
