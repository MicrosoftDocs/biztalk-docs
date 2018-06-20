---
title: "Confirmation Processing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2eccd60f-ae01-4ab8-a35b-d30524016f12
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Confirmation Processing
The sequence of events for confirmation processing is as follows:  
  
1. Establish the synchronization level.  
  
2. Send a confirmation request.  
  
3. Receive data and confirmation request.  
  
4. Respond to the confirmation request.  
  
5. Deallocate the conversation.  
  
   Using confirmation processing, a TP sends a confirmation request with the data; the partner TP confirms receipt of the data or indicates that an error occurred. Each time the two TPs exchange a confirmation request and response, they are synchronized.  
  
> [!NOTE]
>  Although the example in this section does not show this, any TP can send or receive data, regardless of whether the TP is the invoking TP or the invokable TP.  
  
 The following example illustrates confirmation processing.  
  
|Issued by the invoking TP|Issued by the invokable TP|  
|-------------------------------|--------------------------------|  
|TP_STARTED||  
|MC_ALLOCATE||  
|(synclevel=AP_CONFIRM_SYNC_LEVEL)||  
|MC_SEND_DATA||  
|(type=AP_SEND_DATA_CONFIRM)||  
||RECEIVE_ALLOCATE|  
||MC_RECEIVE_AND_WAIT|  
|MC_SEND_DATA||  
|(type=AP_SEND_DATA_DEALLOC_SYNC_LEVEL)||  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(rtn_status=AP_YES)|  
||(what_rcvd= AP_DATA_COMPLETE_CONFIRM_ DEALLOCATE)|  
||MC_CONFIRMED|  
|TP_ENDED|TP_ENDED|  
  
## Establishing the Synchronization Level  
 The **synclevel** parameter of [MC_ALLOCATE](./mc-allocate2.md) determines the synchronization level of the conversation. There are three possible synchronization levels:  
  
-   AP_NONE, under which confirmation processing does not occur.  
  
-   AP_CONFIRM_SYNC_LEVEL, under which the TPs can request confirmation of receipt of data and respond to requests for confirmation of data.  
  
-   AP_SYNCPT, under which the TPs operate under Sync Point Level 2 support for confirmation of receipt of data.  
  
## Sending a Confirmation Request  
 [MC_SEND_DATA](./mc-send-data1.md) with type AP_SEND_DATA_CONFIRM has two effects:  
  
- It flushes the local LU's send buffer and sends any data contained in the buffer to the partner TP.  
  
- It sends a confirmation request that the partner TP receives through the **what_rcvd** parameter of a receive verb.  
  
  After issuing **MC_SEND_DATA**, the local TP waits for confirmation from the partner TP.  
  
## Receiving Data and Confirmation Request  
 The **what_rcvd** parameter of [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md) indicates:  
  
- Status of the data received: complete or incomplete.  
  
- Future processing expected of the local TP.  
  
  In the example, **what_rcvd** is AP_DATA_COMPLETE_CONFIRM, indicating that the status is complete and a confirmation is requested.  
  
## Responding to a Confirmation Request  
 The partner TP issues [MC_CONFIRMED](./mc-confirmed1.md) to confirm receipt of data. This frees the local TP to resume processing.  
  
## Deallocating the Conversation  
 [MC_SEND_DATA](./mc-send-data1.md) sends a confirmation request with the data when all of the following conditions are true:  
  
-   The conversation's synchronization level (established by the **synclevel** parameter of [MC_ALLOCATE](./mc-allocate2.md)) is AP_CONFIRM_SYNC_LEVEL.  
  
-   The type parameter of **MC_SEND_DATA** is set to AP_SEND_DATA_DEALLOC_SYNC_LEVEL.  
  
-   The **what_rcvd** parameter of the final [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md) is AP_DATA_COMPLETE_CONFIRM_DEALLOCATE, indicating that a confirmation of receipt of data is required before APPC will deallocate the conversation. The local TP waits for this confirmation until the partner TP issues [MC_CONFIRMED](./mc-confirmed1.md).