---
title: "Mapped Conversation Example | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13cb8205-33bb-4a4a-b330-25e309bfe6ca
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# An Example of a Mapped Conversation
For background information about mapped conversations, see [Basic and Mapped Conversations Compared](../core/basic-and-mapped-conversations-compared2.md).  
  
 The following example of a mapped conversation shows the APPC verbs used to start a conversation, exchange data, and end the conversation. APPC verb parameters are in parentheses.  
  
|Issued by the invoking TP|Issued by the invokable TP|  
|-------------------------------|--------------------------------|  
|TP_STARTED||  
|MC_ALLOCATE||  
|MC_SEND_DATA||  
|MC_DEALLOCATE||  
|TP_ENDED|RECEIVE_ALLOCATE|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_OK)|  
||(rtn_status=AP_NO)|  
||(what_rcvd=AP_DATA_COMPLETE)|  
||MC_RECEIVE_AND_WAIT|  
||(primary_rc=AP_DEALLOC_NORM)|  
||TP_ENDED|  
  
 The following paragraphs describe the verbs that are used in a mapped conversation.  
  
## Verbs for Starting a Mapped Conversation  
 To start a mapped conversation, the invoking TP issues the following verbs:  
  
- [TP_STARTED](tp-started2.md), which notifies APPC that the local TP is beginning a conversation.  
  
- [MC_ALLOCATE](mc-allocate2.md), which requests that APPC establish a conversation between the local TP and the partner TP.  
  
  The invokable TP issues [RECEIVE_ALLOCATE](receive-allocate1.md), which informs APPC that it is ready to begin a conversation with the invoking TP.  
  
## Verbs for Sending Data in a Mapped Conversation  
 [MC_SEND_DATA](mc-send-data1.md) puts one data record (a record containing application data to be transmitted) in the send buffer of the local LU. Data transmission to the partner TP does not happen until one of the following events occurs:  
  
- The send buffer fills up.  
  
- The sending TP issues a verb that forces APPC to flush the buffer and send data to the partner TP.  
  
  In the preceding example, the send buffer contains both the data record and the [MC_ALLOCATE](./mc-allocate2.md) request (which precedes the data record). Therefore, in the example, [MC_DEALLOCATE](./mc-deallocate2.md) flushes the buffer, sending the **MC_ALLOCATE** request and data record to the partner TP. Other verbs that flush the buffer are [MC_CONFIRM](./mc-confirm2.md) and [MC_FLUSH](./mc-flush1.md).  
  
## Verbs for Receiving Data in a Mapped Conversation  
 The [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md) verb allows a TP to receive a data record or status information. If no data is currently available, the TP waits for data to arrive. For Windows systems, issue **MC_RECEIVE_AND_WAIT** in conjunction with [WinAsyncAPPC](./winasyncappc1.md) rather than the blocking version of this call.  
  
 In the example, the receiving TP issues **MC_RECEIVE_AND_WAIT** twice. The first time, it issues the verb to receive data. When it finishes receiving the complete data record (**what_rcvd** is AP_DATA_COMPLETE), it issues **MC_RECEIVE_AND_WAIT** again to receive a return code. The return code AP_DEALLOC_NORMAL indicates that the conversation has been deallocated.  
  
> [!NOTE]
>  [MC_RECEIVE_IMMEDIATE](./mc-receive-immediate2.md) performs the same function as **MC_RECEIVE_AND_WAIT**, except that it does not wait if data is not currently available from the partner TP. Instead, it returns a no-data-available response to the calling TP.  
  
## Verbs for Ending a Mapped Conversation  
 To end a mapped conversation, one of the TPs issues [MC_DEALLOCATE](./mc-deallocate2.md), which causes APPC to deallocate the conversation between the two TPs.  
  
 After the conversation has been deallocated, both TPs issue [TP_ENDED](./tp-ended1.md).  
  
> [!NOTE]
>  A TP can participate in multiple conversations simultaneously. In this case, the TP issues **TP_ENDED** after all conversations have been deallocated.