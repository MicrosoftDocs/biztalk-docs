---
title: "Presentation Header Support in Data Transfers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c93955c-1e31-4140-8ec4-b7c7b399b117
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Presentation Header Support in Data Transfers
For basic conversations, Sync Point commands are sent by means of presentation headers (PS) across LU 6.2 conversations using the [SEND_DATA](./send-data1.md) or [MC_SEND_DATA](./mc-send-data1.md) verb. All presentation headers contain length fields that specify a length of 1, which is usually illegal. To support Sync Point conversations, the following modifications are made to the Host Integration Server presentation services component:  
  
- On basic conversations with a **synclevel** of AP_SYNCPT, data transferred specifying a general data stream (GDS) variable length of 1 will not be rejected. If the **synclevel** is not AP_SYNCPT, they will be rejected as before.  
  
- On mapped conversations, PS headers will not be wrapped as mapped conversation application data logical records (with GDS identifier 0x12FF) when they are sent, or have the GDS header stripped off when they are received.  
  
- On mapped conversations, it is the responsibility of the application to provide the complete PS header including the length field. Similarly, the length field will be included in PS header data returned by receive verbs.  
  
  To achieve the latter the [MC_SEND_DATA](./mc-send-data1.md) verb and the receive verbs ([MC_RECEIVE_AND_POST](./mc-receive-and-post2.md), [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md), and [MC_RECEIVE_IMMEDIATE](./mc-receive-immediate2.md)) require modifications as follows:  
  
- A new parameter, **data_type**, is added to the **MC_SEND_DATA** verb. When this is set to AP_APPLICATION (the default, 0x00), the data is sent as application data (GDS identifier 0x12FF) as usual. When it is set to AP_PS_HEADER, the data is sent as described above.  
  
- The following two new values are added for the **what_rcvd** member of the receive verbs to specify that the received data is a PS header:  
  
   AP_PS_HEADER_COMPLETE  
  
   AP_PS_HEADER_INCOMPLETE  
  
- If an application issues a receive verb with **rtn_status** set to AP_YES, Host Integration Server will return status in combination with AP_PS_HEADER_COMPLETE, with the exception of AP_DEALLOCATE_NORMAL and AP_CONFIRM_DEALLOCATE. This is to prevent the conversation being prematurely disconnected from the LU 6.2 session when a COMMIT PS header arrives with the end of conversation indication.  
  
  It is the responsibility of the vendor-supplied Sync Point support component to convert these PS headers into the appropriate Sync Point return codes (for example, TAKE_SYNCPT).