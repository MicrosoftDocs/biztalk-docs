---
title: "Error - Input for Mass Copy Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.massCopyInputNotValid"
ms.assetid: 141c45cd-79da-4f99-abb0-60a88dfcab76
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Input for Mass Copy Functoid Not Valid
**Error Code**  
  
 btm1069  
  
 **Explanation**  
  
 The input parameter for the relevant **Mass Copy** functoid is not valid or too many input parameters for the relevant **Mass Copy** functoid have been specified. **Mass Copy** functoids must have exactly one input: a link from a **Record** node in the source schema.  
  
 **User Action**  
  
 Reconfigure the relevant **Mass Copy** functoid such that it has a single input parameter from a **Record** node in the source schema.