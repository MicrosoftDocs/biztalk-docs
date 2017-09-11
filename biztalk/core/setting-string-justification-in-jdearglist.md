---
title: "Setting String Justification in Jdearglist | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "jdearglist.txt, setting string justification"
  - "strings, configuring"
  - "strings, right-justified"
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting String Justification in Jdearglist
To configure certain string arguments as right-justified (and left padded) in the JD Edwards OneWorld jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.  
  
 You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration. The instructions for updating the jdearglist.txt file are outlined in [Handling String Values](../core/handling-string-values1.md).  
  
 If you receive a jdearglist.txt warning message in the audit log, it informs you that the jdearglist.txt is missing. If you run the SalesOrder or PurchaseOrder business functions, you must have the file in your PATH, or it will not work.  
  
## See Also  
 [Administering BizTalk Adapter for JD Edwards OneWorld](../core/administering-biztalk-adapter-for-jd-edwards-oneworld.md)