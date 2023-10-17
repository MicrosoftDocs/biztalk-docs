---
description: "Learn more about: Error - Output Link For XSLT Scripting Functoid Not Valid"
title: "Error - Output Link For XSLT Scripting Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.outputLinkForXsltNotValid"
ms.assetid: cdf8e779-6cf6-4d9c-8655-f8b406498fb7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Output Link For XSLT Scripting Functoid Not Valid
**Error Code**  
  
 btm1075  
  
 **Explanation**  
  
 The output link of the relevant **Scripting** functoid configured to use inline XSLT or an XSLT Call Template is not valid. The output of such **Scripting** functoids must be connected directly to a node in the destination schema (and not to another functoid, for example).  
  
 **User Action**  
  
 Ensure that you connect the output link from the relevant **Scripting** functoid directly to a node in the destination schema.
