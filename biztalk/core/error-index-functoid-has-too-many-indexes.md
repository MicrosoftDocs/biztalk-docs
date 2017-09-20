---
title: "Error - Index Functoid Has Too Many Indexes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.indexFunctoidHasTooManyIndices"
ms.assetid: 5dd2d5b4-3f7a-45be-b6f4-708b0a76805a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Index Functoid Has Too Many Indexes
**Error Code**  
  
 btm1016  
  
 **Explanation**  
  
 The indicated **Index** functoid has too many index input parameters specified. The number of index input parameters must not exceed the number of ancestor looping **Record** nodes within which the **Field** node specified as the first input parameter is nested.  
  
 **User Action**  
  
 Select the indicated **Index** functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid> Functoid** dialog box, delete the excess index input parameters by selecting and clicking the  ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") button for each of them.