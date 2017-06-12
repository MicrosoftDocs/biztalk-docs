---
title: "Process Manager Logic | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, processing"
  - "processing, processing logic"
ms.assetid: 6b69fc71-0f01-4513-9361-d7787d0cde6d
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Process Manager Logic
This section describes how the process manager, the **OrderManager** orchestration, processes orders. It describes key fields in the various order messages and follows new and updated orders through the orchestration.  
  
 The **OrderManager** orchestration coordinates subordinate orchestrations to process the order. You can add, delete, or modify these stages without having to change the **OrderManager**. The **OrderManager** does much of the coordination through custom messages defined by .NET classes. For a list of all messages in the solution, see [Message Reference for the Business Process Management Solution](../core/message-reference-for-the-business-process-management-solution.md). For information about defining message types with .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
> [!NOTE]
>  Because of the size and scope of **OrderManager**, you may want to read these sections, especially the second, with the orchestration open in Microsoft Visual Studio.  
  
## In This Section  
  
-   [Key Messages and Fields](../core/key-messages-and-fields.md)  
  
-   [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md)