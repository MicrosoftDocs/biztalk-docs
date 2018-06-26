---
title: "Mapped Conversation (CPI-C) Example | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e07e8123-9ca3-4cf3-ba27-853a5fd9a56a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# An Example of a Mapped Conversation (CPI-C)
The following example of a mapped conversation shows the Common Programming Interface for Communications (CPI-C) calls used to start a conversation, exchange data, and end the conversation. Call parameters are in parentheses.  
  
|Issued by the invoking TP|Issued by the invokable TP|  
|-------------------------------|--------------------------------|  
|Initialize_Conversation||  
|Allocate||  
|Send_Data||  
|Deallocate|Accept_Conversation|  
||Receive|  
||(data_received=|  
||CM_COMPLETE_DATA_RECEIVED)|  
||(*return_code*=|  
||CM_DEALLOCATED_NORMAL)|  
  
 The following paragraphs describe the calls that are used in a mapped conversation.  
  
## Calls for Starting a Mapped Conversation  
 To start a conversation, the invoking transaction program (TP) issues the following calls:  
  
- [Initialize_Conversation](initialize-conversation-cpi-c-1.md), which requests CPI-C to set the values defining the characteristics of the conversation. The **Initialize_Conversation** call specifies a symbolic destination name that is associated with an entry in a side information table in memory. The side information specifies partner TP, partner LU, mode, security, and so on.  
  
- [Allocate](allocate-cpi-c-2.md), which requests that CPI-C establish a conversation between the invoking TP and the invokable TP.  
  
  The invokable TP issues the [Accept_Conversation](accept-conversation-cpi-c-2.md) call, which informs CPI-C that it is ready to begin a conversation with the invoking TP.  
  
## Calls for Sending Data in a Mapped Conversation  
 The [Send_Data](send-data-cpi-c-2.md) call puts one data record (a record containing application data to be transmitted) in the send buffer of the local logical unit (LU). Data transmission to the partner TP does not happen until one of the following events occurs:  
  
- The send buffer fills up.  
  
- The sending TP makes a call that forces CPI-C to flush the buffer and send data to the partner TP.  
  
  In addition to the data record, the send buffer also contains the allocation request (which precedes the data record).  
  
  In the preceding example, [Deallocate](deallocate-cpi-c-1.md) flushes the send buffer, sending the allocation request and data to the partner TP. Other calls that flush the buffer are [Confirm](confirm-cpi-c-2.md) and [Flush](flush-cpi-c-2.md).  
  
## Calls for Receiving Data in a Mapped Conversation  
 The **Receive** call receives the data record and status information from the partner TP. If no data or status information is currently available, the local TP, by default, waits for data to arrive.  
  
 The *data_received* parameter of [Receive](receive-cpi-c-2.md) tells the program whether it received data and if so, whether or not the data is complete.  
  
## Calls for Ending a Mapped Conversation  
 To end a conversation, one of the TPs issues [Deallocate](deallocate-cpi-c-1.md), which causes CPI-C to deallocate the conversation between the two TPs.