---
title: "Error - Second Input to Cumulative Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.secondInputToCumulativeNotValid"
ms.assetid: e41a58a7-e0a2-4284-bd19-279578a8915d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Second Input to Cumulative Functoid Not Valid
**Error Code**  
  
 btm1031  
  
 **Explanation**  
  
 The indicated **Cumulative** functoid has a second input parameter that is not valid. The second input parameter to cumulative functoids must be a positive integer that indicates the range within the source schema over which the accumulation will be performed.  
  
 **User Action**  
  
 Select the indicated **Cumulative** functoid, click the ellipsis (**...**) button associated with the **Order Functoid Inputs** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid> Functoid** dialog box, ensure that the second input parameter, if any, is a positive integer.