---
description: "Learn more about: Validation with Business Rules"
title: "Validation with Business Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validating, process management solutions"
  - "process management solution tutorial, validating"
  - "business rules, validating"
  - "process management solution tutorial, business rules"
ms.assetid: a67f3781-629a-4157-9a27-3b73d7a5a3a8
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validation with Business Rules
A common way to do validation is to construct a set of business rules using the Business Rules Framework. Then you use the Call Rules shape in the orchestration where you want to perform validation.  
  
 In the business process management application, the **Validation** orchestration uses business rules to test the validity of the order.  
  
 Using the Business Rules Framework enables you to change the rules without recompiling and redeploying the **Validation** orchestration. The trade-off is that for simple sets of rules, you may be able to save processing time by coding the logic in the orchestration.  
  
 For more information about using the Business Rules Framework, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md). For more information about the Call Rules shape, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)
