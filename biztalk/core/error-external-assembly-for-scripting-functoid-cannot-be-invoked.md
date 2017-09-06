---
title: "Error - External Assembly for Scripting Functoid Cannot Be Invoked | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.cannotInvokeExternalAssembly"
ms.assetid: 30d97b05-2cbf-44a5-b219-3a5ae17fc597
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - External Assembly for Scripting Functoid Cannot Be Invoked
**Error Code**  
  
 btm1067  
  
 **Explanation**  
  
 The external assembly method that is associated with the relevant **Scripting** functoid cannot be invoked. Although not required for map compilation, the Test Map operation requires that such external assemblies be present in the global assembly cache (GAC). Normal, run time operation also requires that external assemblies be present in the GAC.  
  
 **User Action**  
  
 Ensure that the external assembly referenced by the relevant **Scripting** functoid is in the GAC.