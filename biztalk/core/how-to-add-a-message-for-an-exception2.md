---
title: "How to Add a Message for an Exception2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, adding messages"
  - "messages, exceptions"
  - "exception handling, adding messages"
  - "fault messages, adding"
ms.assetid: 9d8a3801-78cd-4c18-8deb-3fbe4a49a2f9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Message for an Exception
When you first create a port to the back-end system, it contains a request and a response. You must add a message so that you can assign it to the fault.  
  
### To add a fault message  
  
1. In the **Orchestration View** window, right-click **Messages**, and then select **New Message**.  
  
    This creates Message_3, which you can assign specifically to the fault.  
  
2. Right-click **Message_3**, and select **Properties**.  
  
3. Set the **Message Type** as follows: select **.NET Classes**, and then select **System,String**  
  
   ![](../core/media/jdeoneworld-03-addscope.gif "JdeOneWorld_03_addscope")  
  
## See Also  
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling1.md)