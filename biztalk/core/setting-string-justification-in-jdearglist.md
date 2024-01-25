---
title: "Set string justification in JD Edwards OneWorld adapter"
description: Update jdearglist file to use the JD Edwards OneWorld adapter in a BizTalk Server orchestration
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Set string Justification in Jdearglist

## Overview
To configure certain string arguments as right-justified (and left padded) in the JD Edwards OneWorld jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.  
  
 You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration. The instructions for updating the jdearglist.txt file are outlined in [Handling String Values](../core/handling-string-values1.md).  
  
 If you receive a jdearglist.txt warning message in the audit log, it informs you that the jdearglist.txt is missing. If you run the SalesOrder or PurchaseOrder business functions, you must have the file in your PATH, or it will not work.  
  
## See Also  
[Use BizTalk Server Exception Handling](using-biztalk-server-exception-handling1.md)