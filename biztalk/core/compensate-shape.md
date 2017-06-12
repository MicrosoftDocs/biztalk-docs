---
title: "Compensate Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.compensate"
ms.assetid: cc75193c-0193-4891-86e9-f887e5008f4e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Compensate Shape
If you are using nested transactions, you can add a **Compensate** shape in the compensation block or an exception block of a transaction scope, so your orchestration can explicitly perform compensation on a nested transaction. You specify the transaction to compensate, and any compensation code in the nested transaction that will be run. If you want to compensate more than one nested transaction, you add an additional **Compensate** shape for each transaction.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Compensation** property|From the drop-down list, select a transaction on which compensation will be done.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Compensate Shape](../core/how-to-configure-the-compensate-shape.md)