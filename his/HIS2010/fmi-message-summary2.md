---
title: "FMI Message Summary2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85ec005b-0aed-4b49-a25c-551589594bbd
caps.latest.revision: 3
---
# FMI Message Summary
This section lists each of the messages used at the function management interface (FMI) and gives a reference to a topic in the section where each message is described. The formats of the messages are given in [FMI Message Formats](../HIS2010/fmi-message-formats1.md).  
  
 For each message the direction of flow is indicated. IN means from the application to the local node, and OUT means from the local node to the application. The connection on which the message flows is also given.  
  
|Message|Direction|Connection|Reference|  
|-------------|---------------|----------------|---------------|  
|**Open(SSCP) Request**|IN|SSCP|[Opening the SSCP Connection](../HIS2010/opening-the-sscp-connection2.md)|  
|**Open(SSCP) Response**|OUT|SSCP|[Opening the SSCP Connection](../HIS2010/opening-the-sscp-connection2.md)|  
|**Open(SSCP) Error Response**|OUT|SSCP|[Opening the SSCP Connection](../HIS2010/opening-the-sscp-connection2.md)|  
|**Open(PLU) Request**|OUT|PLU|[Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)|  
|**Open(PLU) OK Response**|IN|PLU|[Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)|  
|**Open(PLU) Error Response**|IN|PLU|[Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)|  
|**Open(PLU) OK Confirm**|OUT|PLU|[Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)|  
|**Open(PLU) Error Confirm**|OUT|PLU|[Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)|  
|**Close(SSCP) Request**|IN|SSCP|[Closing the SSCP Connection](../HIS2010/closing-the-sscp-connection1.md)|  
|**Close(SSCP) OK Response**|OUT|SSCP|[Closing the SSCP Connection](../HIS2010/closing-the-sscp-connection1.md)|  
|**Close(PLU) Request**|IN/OUT|PLU|[Closing the PLU Connection](../HIS2010/closing-the-plu-connection2.md)|  
|**Close(PLU) OK Response**|IN/OUT|PLU|[Closing the PLU Connection](../HIS2010/closing-the-plu-connection2.md)|  
|**Data-FMI**|IN/OUT|SSCP/PLU|[Data Flow](../HIS2010/data-flow2.md)|  
|**Status-Acknowledge(Ack)**|IN/OUT|SSCP/PLU|[Data Flow](../HIS2010/data-flow2.md), [Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Acknowledge(Nack-1)**|IN/OUT|SSCP/PLU|[Data Flow](../HIS2010/data-flow2.md), [Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Acknowledge(Nack-2)**|OUT|SSCP/PLU|[Inbound Data](../HIS2010/inbound-data1.md)|  
|**Status-Control(CLEAR) Request**|OUT|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(CLEAR) Ack**|IN|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(CLEAR) Nack-1**|IN|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(SDT) Request**|OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(RQR) Request**|IN|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(RQR) Ack**|OUT|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(RQR) Nack-1**|OUT|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(RQR) Nack-2**|OUT|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(STSN) Request**|OUT|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(STSN) Ack**|IN|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(STSN) Nack-1**|IN|PLU|[Recovery](../HIS2010/recovery2.md)|  
|**Status-Control(CANCEL) Request**|IN/OUT|PLU|[Outbound Chaining](../HIS2010/outbound-chaining1.md), [Inbound Chaining](../HIS2010/inbound-chaining2.md)|  
|**Status-Control(CANCEL) Ack**|IN/OUT|PLU|[Outbound Chaining](../HIS2010/outbound-chaining1.md), [Inbound Chaining](../HIS2010/inbound-chaining2.md)|  
|**Status-Control(CANCEL) Nack-1**|IN/OUT|PLU|[Outbound Chaining](../HIS2010/outbound-chaining1.md), [Inbound Chaining](../HIS2010/inbound-chaining2.md)|  
|**Status-Control(CANCEL) Nack-2**|OUT|PLU|[Inbound Chaining](../HIS2010/inbound-chaining2.md)|  
|**Status-Control(LUSTAT) Request**|IN/OUT|PLU|[LUSTATs](../HIS2010/lustats]2.md)|  
|**Status-Control(LUSTAT) Ack**|IN/OUT|PLU|[LUSTATs](../HIS2010/lustats]2.md)|  
|**Status-Control(LUSTAT) Nack-1**|IN/OUT|PLU|[LUSTATs](../HIS2010/lustats]2.md)|  
|**Status-Control(LUSTAT) Nack-2**|OUT|PLU|[LUSTATs](../HIS2010/lustats]2.md)|  
|**Status-Control(SIGNAL) Request**|IN/OUT|PLU|[Direction](../HIS2010/direction2.md)|  
|**Status-Control(SIGNAL) Ack**|OUT|PLU|[Direction](../HIS2010/direction2.md)|  
|**Status-Control(SIGNAL) Nack-1**|OUT|PLU|[Direction](../HIS2010/direction2.md)|  
|**Status-Control(SIGNAL) Nack-2**|OUT|PLU|[Direction](../HIS2010/direction2.md)|  
|**Status-Control(RSHUTD) Request**|IN|PLU|[Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)|  
|**Status-Control(RSHUTD) Ack**|OUT|PLU|[Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)|  
|**Status-Control(RSHUTD) Nack-1**|OUT|PLU|[Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)|  
|**Status-Control(RSHUTD) Nack-2**|OUT|PLU|[Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)|  
|**Status-Control(BID) Request**|OUT|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(BID) Ack**|IN|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(BID) Nack-1**|IN|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(CHASE) Request**|IN/OUT|PLU|[Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Control(CHASE) Ack**|IN/OUT|PLU|[Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Control(CHASE) Nack-1**|IN/OUT|PLU|[Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Control(CHASE) Nack-2**|OUT|PLU|[Confirmation and Rejection of Data](../HIS2010/confirmation-and-rejection-of-data]2.md)|  
|**Status-Control(SHUTC) Request**|IN|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(SHUTC) Ack**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(SHUTC) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(SHUTC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(SHUTD) Request**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(RTR) Request**|IN|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(RTR) Ack**|OUT|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(RTR) Nack-1**|OUT|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(RTR) Nack-2**|OUT|PLU|[Brackets](../HIS2010/brackets2.md)|  
|**Status-Control(QC) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QC) Ack**|IN/OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QC) Nack-1**|IN/OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QEC) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QEC) Ack**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QEC) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(QEC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(RELQ) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(RELQ) Ack**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(RELQ) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Control(RELQ) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)|  
|**Status-Error**|OUT|SSCP/PLU|[Status-Error Message](../HIS2010/status-error-message2.md)|  
|**Status-Resource**|IN|PLU|[Pacing and Chunking](../HIS2010/pacing-and-chunking2.md)|  
|**Status-Session**|OUT|SSCP/PLU|[Status-Session Message](../HIS2010/status-session-message2.md), [Status-Session Codes](../HIS2010/status-session-codes2.md)|  
|**Status-RTM**|OUT|SSCP|[RTM Parameters](../HIS2010/rtm-parameters]1.md)|  
  
 The following table lists the messages that are used for LUA only.  
  
|Message|Direction|Connection|Reference|  
|-------------|---------------|----------------|---------------|  
|**Status-Acknowledge(ACKLUA)**|OUT|SSCP/PLU|[Inbound Data from LUA Applications](../HIS2010/inbound-data-from-lua-applications2.md)|  
|**Status-Control(...) ACKLUA**|OUT|PLU|[Inbound Data from LUA Applications](../HIS2010/inbound-data-from-lua-applications2.md)|  
|**Status-Control(CRV) Request**|OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(CRV) Ack**|IN|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(CRV) Nack-1**|IN|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(BIS) Request**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(BIS) Ack**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(BIS) Nack-1**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(SBI) Request**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(SBI) Ack**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
|**Status-Control(SBI) Nack-1**|IN/OUT|PLU|[Status-Control Message](../HIS2010/status-control-message2.md)|  
  
## See Also  
 [FMI Concepts](../HIS2010/fmi-concepts2.md)   
 [SSCP Connection](../HIS2010/sscp-connection2.md)   
 [PLU Connection](../HIS2010/plu-connection1.md)   
 [Data Flow](../HIS2010/data-flow2.md)   
 [Status Messages](../HIS2010/status-messages1.md)   
 [FMI Message Summary](#_sna_fmi_message_summary_3270)