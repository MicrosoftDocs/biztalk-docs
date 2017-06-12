---
title: "Label (Link Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Label property, schema links"
ms.assetid: 1565c75f-fea9-48ec-b8f3-cb903929937a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Label (Link Property)
Use the **Label** property to provide a name for the selected link that makes sense to you in the context of its use.  
  
## Category  
 General  
  
## Allowed Values  
 Any string. The string should describe this link, generally based on where it originates in the source schema or from another functoid.  
  
## Default Value  
 None.  
  
## Remarks  
 The maximum number of characters allowed is 256.  
  
 Configuring this property is helpful when the link is used as an input other than the first or second input to the **Table Looping** functoid. This is because the descriptive value you provide for the **Label** property of the link is shown in the table cell drop-down lists in the **Table Looping Configuration** dialog box. If you do not provide a value for the **Label** property of such links, the value of the **Link Source** property for the link is shown; when this value is an XPath value, as opposed to a functoid type, it is more difficult to determine the source of the link when choosing a link value for the table cell.  
  
 For more information about table-driven looping, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).  
  
## See Also  
 [Link Properties](../core/link-properties.md)