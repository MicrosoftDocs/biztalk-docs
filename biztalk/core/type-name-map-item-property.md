---
title: "Type Name (Map Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Type Name property [maps]"
ms.assetid: 68881504-1571-4502-9c41-b3853985769e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Type Name (Map Item Property)
Use the **Type Name** property to specify an alternative name for the compiler-generated managed type that corresponds to a map.  
  
## Category  
 Advanced  
  
## Allowed Values  
 Valid type name identifiers can be entered as values for this property.  
  
## Default Value  
 The original name of the map when it was created, without the file extension portion of the name.  
  
## Remarks  
 If you change the value of this property, you must make sure that you change references to the selected map in any orchestrations that reference it.  
  
 To avoid compilation errors, you must make sure that the value of the [Fully Qualified Name](../core/fully-qualified-name-map-item-property.md) property, (created by concatenating the value of the [Namespace](../core/namespace-map-item-property.md) property, a period (.) character, and the value of this property) is unique within the BizTalk project.