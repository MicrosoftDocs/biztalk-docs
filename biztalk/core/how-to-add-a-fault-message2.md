---
description: "Learn how to add a fault message in the Orchestration View of BizTalk Server."
title: "How to Add a Fault Message2"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add a Fault Message

When you create a port to the back-end system, it contains a request and a response. You must add a message so that you can assign it to the fault.  
  
### To add a fault message  
  
1.  In the **Orchestration View** window, right-click **Messages**, and select **New Message**.  
  
     This creates Message_3, which you can assign specifically to the fault.  
  
2.  Right-click Message_3, and select **Properties**.  
  
3.  In the **Properties** dialog box, set the **Message Type**.  
  
     Select **.NET Classes** and then select **SystemString**.  
  
## See Also  
 [Using BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling3.md)
