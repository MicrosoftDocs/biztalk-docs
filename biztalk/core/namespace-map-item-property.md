---
title: "Namespace (Map Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Namespace property [maps]"
ms.assetid: 177a6d92-4b6f-46f8-b7e6-605028234726
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Namespace (Map Item Property)
Use the **Namespace** property to specify an alternative .NET namespace for a map.  
  
## Category  
 Advanced  
  
## Allowed Values  
 Valid namespace identifiers can be entered as the value of this property.  
  
## Default Value  
 The name of the BizTalk project in which the map was originally created.  
  
## Remarks  
 If you change the value of this property, you must make sure that you change references to the selected map in any orchestrations that reference it.  
  
 To avoid compilation errors, you must make sure that the value of the [Fully Qualified Name](../core/fully-qualified-name-map-item-property.md) property (created by concatenating the value of this property, a period (.) character, and the value of the [Type Name](../core/type-name-map-item-property.md) property) is unique within the BizTalk project.