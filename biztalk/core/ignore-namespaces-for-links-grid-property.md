---
title: "Ignore Namespaces for Links (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ignore Namespaces for Links property [grid pages]"
ms.assetid: a139416b-da76-4aa8-9058-0c3979a39bb9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ignore Namespaces for Links (Grid Property)
Use the **Ignore Namespaces for Links** property to indicate whether the links stored in the map contain any references to the namespaces used in the schemas.  
  
## Category  
 General  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**True**|Specifies that the links in the map do not contain any references to the namespaces used in the source or destination schemas, thereby protecting the links from changes made to those schema namespaces outside the map.|  
|**False**|Specifies that the links in the map contain references to the namespaces used in the source and destination schemas, thereby making the links sensitive to changes made to those schema namespaces outside the map.|  
  
## Default Value  
 **True**  
  
## Remarks  
 If the value of this property is set to **True**, changes to the namespaces in the source and destination schemas used by the map will not invalidate its links.  
  
 The only situation in which you should set the value of this property to **False** is when either your source or destination schema contains sibling nodes of the same type and with the same name, but with different namespaces. In such cases, the namespace designator in links is necessary to find the correct source or destination node for the link in the produced XSLT.  
  
> [!NOTE]
>  You can undo or redo the **Ignore Namespaces for Links** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)