---
title: "Version (Grid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Version property"
ms.assetid: c19cde4b-1483-4acd-9079-6417bdd48e18
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Version (Grid Property)
Use the **Version** property to specify version "1.0" in relation to the "xml" output method, which appears in the output XML declaration as:  
  
```  
<?xml version='1.0' ?>  
```  
  
## Category  
 Custom Header  
  
## Allowed Values  
 Any string, unenforced by BizTalk Mapper. However, version 1.0 is the only supported version at this time.  
  
## Default Value  
 1.0  
  
## Remarks  
 This property provides a value for the **version** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.  
  
> [!NOTE]
>  You cannot undo or redo the **Version** property.  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)