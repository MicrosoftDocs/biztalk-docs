---
title: "Basic and Mapped Conversations Compared (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5193e3a9-8b9f-46f1-aead-37b04d9276d5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic and Mapped Conversations Compared (CPI-C)
The following table offers some guidelines for choosing between basic and mapped conversations for your transaction programs (TPs). The default for conversation type is mapped. To change to a basic conversation, use [Set_Conversation_Type](../core/set-conversation-type-cpi-c-2.md), and specify CM_BASIC_CONVERSATION for the *conversation_type*. For definitions of basic and mapped conversations, see [Fundamental Terms for TPs and LUs](../core/fundamental-terms-for-tps-and-lus-cpi-c-2.md).  
  
|Characteristic|Basic conversations|Mapped conversations|  
|--------------------|-------------------------|--------------------------|  
|Common use|Generally used for service TPs.|Generally used for application TPs.|  
|Partnering|Must be used to communicate with an existing TP that uses basic verbs.|Must be used to communicate with an existing TP that uses mapped verbs.|  
|Sending and receiving method|Before a TP can begin a send operation, it must convert data records into logical records. The TP does this by adding a 2-byte prefix that indicates the length of the record. A TP can send several logical records at one time.<br /><br /> When a partner TP receives logical records, it must reconstruct them into usable data records. For more information, see [Logical Records Used in Basic Conversations](../core/logical-records-used-in-basic-conversations-cpi-c-2.md).|A TP sends data one record at a time. Neither the sending TP nor the receiving TP needs to convert data records between different forms.|  
|Abnormal termination|In the[Deallocate](../core/deallocate-cpi-c-2.md) call, a TP can indicate whether an error or ABEND (abnormal program termination) was caused by a TP or by a program using the TP.|A TP can indicate an error or ABEND, but cannot tell whether a problem was caused by a TP or by a program using a TP.|  
|ABEND|A TP can indicate whether an ABEND was caused by a time-out or by a critical error.|A TP cannot indicate the cause of an ABEND.|  
|Error logging|For an error or ABEND, a TP can send an error message, in the form of a general data stream (GDS) error log variable, to the local log and to the partner logical unit (LU).|For an error or ABEND, a TP cannot send an error message to the local log or to the partner LU.|  
  
 This section contains:  
  
-   [Logical Records Used in Basic Conversations](../core/logical-records-used-in-basic-conversations-cpi-c-2.md)  
  
-   [An Example of a Mapped Conversation](../core/an-example-of-a-mapped-conversation-cpi-c-1.md)