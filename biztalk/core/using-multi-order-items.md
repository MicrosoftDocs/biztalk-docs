---
description: "Learn more about: Using Multi-Order Items"
title: "Using Multi-Order Items"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using Multi-Order Items
Due to the structure of the JD Edwards OneWorld API, if you want to use multi-order numbers with BizTalk Server, you must make multiple edit line calls in your orchestration to add those line items in an orchestration. For example, a multi-order item might contain a header with a single order number, and detail that includes several items orders (like Toy 1EA, Gloves 2EA).  
  
 To use multiple edit line calls, it is the responsibility of the BizTalk Server developer to structure them. The developer should create an internal loop in the orchestration to make those calls.  
  
 The JD Edwards OneWorld system supports multiple edit line calls, but the API does not. If you look at the structure of the Edit Line method, it is a flat structure and not a sequence. Therefore, you must call the function every time you want to insert a line item.  
  
## See Also  
 [Planning and Architecture](../core/planning-and-architecture17.md)
