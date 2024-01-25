---
description: "Learn more about: Error - Duplicate Property Field Promotion"
title: "Error - Duplicate Property Field Promotion"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.dupPropFieldPromo"
---
# Error - Duplicate Property Field Promotion
**Error Code**  
  
 BEC2016  
  
 **Explanation**  
  
 Multiple nodes in this schema are being promoted as Property Fields to the same **Field Element** node in the same property schema.  
  
 **User Action**  
  
 Use the **Property Fields** tab of the **Promote Properties** dialog box, accessed through the **Promote Properties** property of the **Schema** node, to delete all but one of the Property Field promotions that are associated with the same **Field Element** node in the property schema. You may want to add new **Field Element** nodes to the property schema so that the deleted promotions can be re-promoted to their own **Field Element** nodes.
