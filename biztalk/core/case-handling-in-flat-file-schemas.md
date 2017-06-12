---
title: "Case Handling in Flat File Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f2b56d2-03fa-41e9-ae28-3275b404d4db
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Case Handling in Flat File Schemas
You can use the [Case](../core/case-node-property-of-flat-file-schemas.md) property to perform case conversion of flat file data when being translated from its equivalent XML format. When the flat file assembler translates an XML message into its equivalent flat file format, and the **Case** property is set to either **Uppercase** or **Lowercase**, all data governed by the corresponding schema will be converted to uppercase or lowercase, respectively, during the translation.  
  
 When the **Case** property is set to **(Default)**, no case conversion is performed.  
  
## See Also  
 [Considerations When Creating Flat File Message Schemas](../core/considerations-when-creating-flat-file-message-schemas.md)   
 [Case (Node Property of Flat File Schemas)](../core/case-node-property-of-flat-file-schemas.md)