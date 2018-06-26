---
title: "Implied Forget2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32c93e3e-d620-46e4-8b66-181bbf111f64
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Implied Forget
LU 6.2 Sync Point sessions can use an optimization of the architected message flows known as implied forget. When the protocol specifies that a FORGET presentation header (PS) is required, the next data flow on the session implies that a FORGET has been received, even though it has not. In the normal situation, the TP is aware of the next data flow when data is received or sent on one of its Sync Point conversations.  
  
 However it is possible that the last message that flows is caused by the conversation being deallocated. In this case, the TP is unaware when the next data flow on the session occurs. To provide the TP with this notification, the [DEALLOCATE](./deallocate2.md) and [MC_DEALLOCATE](./mc-deallocate2.md) verbs are modified to allow the TP to register a callback function which will be called:  
  
- On the first normal flow transmission (request or response) over the session used by the conversation.  
  
- If the session is unbound before any other data flows.  
  
- If the session is terminated abnormally due to a data link control (DLC) outage.  
  
  The callback procedure can take any name because the address of the procedure is passed into the APPC DLL.  
  
  Note that the **DEALLOCATE** and **MC_DEALLOCATE** verbs will probably complete before the callback routine is called. The conversation is considered to be in RESET state and no further verbs can be issued using the conversation identifier. If the application issues a [TP_ENDED](./tp-ended1.md) verb before the next data flow on the session, the callback routine will not be invoked.  
  
  The [DEALLOCATE](./deallocate2.md) and [MC_DEALLOCATE](./mc-deallocate2.md) verbs are modified as follows to support implied forget:  
  
- A new member, **callback**, is added to allow the TP to specify the address of the function to call on the next data flow on the session being used by the conversation being deallocated. If this member is NULL, no notification will be provided. A vendor would normally supply this callback function.  
  
- The **DEALLOCATE** and **MC_DEALLOCATE** verbs also contain a correlator member which is returned as one of the parameters when the callback function is invoked. The application can use this parameter in any way (for example, as a pointer to a control block within the application).  
  
  Host Integration Server allows TPs to deallocate conversations immediately after sending data by specifying the **type** member in the [SEND_DATA](./send-data1.md)and [MC_SEND_DATA](./mc-send-data1.md)verbs as AP_SEND_DATA_DEALLOC_FLUSH, AP_SEND_DATA_DEALLOC_SYNC_LEVEL, AP_SEND_DATA_DEALLOC_ABEND, and AP_SEND_DATA_DEALLOC_CONFIRM. However, the **SEND_DATA** and **MC_SEND_DATA** verbs do not contain the implied forget callback function. TPs wishing to receive implied forget notification must issue a [DEALLOCATE](./deallocate2.md) or [MC_DEALLOCATE](./mc-deallocate2.md) verb explicitly.