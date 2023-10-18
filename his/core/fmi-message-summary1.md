---
description: "Learn more about: FMI Message Summary"
title: "FMI Message Summary1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FMI Message Summary
This section lists each of the messages used at the function management interface (FMI) and gives a reference to a topic in the section where each message is described. The formats of the messages are given in [FMI Message Formats](./fmi-message-formats2.md).  
  
 For each message the direction of flow is indicated. IN means from the application to the local node, and OUT means from the local node to the application. The connection on which the message flows is also given.  
  
|Message|Direction|Connection|Reference|  
|-------------|---------------|----------------|---------------|  
|**Open(SSCP) Request**|IN|SSCP|[Opening the SSCP Connection](../core/opening-the-sscp-connection1.md)|  
|**Open(SSCP) Response**|OUT|SSCP|[Opening the SSCP Connection](../core/opening-the-sscp-connection1.md)|  
|**Open(SSCP) Error Response**|OUT|SSCP|[Opening the SSCP Connection](../core/opening-the-sscp-connection1.md)|  
|**Open(PLU) Request**|OUT|PLU|[Opening the PLU Connection](../core/opening-the-plu-connection1.md)|  
|**Open(PLU) OK Response**|IN|PLU|[Opening the PLU Connection](../core/opening-the-plu-connection1.md)|  
|**Open(PLU) Error Response**|IN|PLU|[Opening the PLU Connection](../core/opening-the-plu-connection1.md)|  
|**Open(PLU) OK Confirm**|OUT|PLU|[Opening the PLU Connection](../core/opening-the-plu-connection1.md)|  
|**Open(PLU) Error Confirm**|OUT|PLU|[Opening the PLU Connection](../core/opening-the-plu-connection1.md)|  
|**Close(SSCP) Request**|IN|SSCP|[Closing the SSCP Connection](../core/closing-the-sscp-connection2.md)|  
|**Close(SSCP) OK Response**|OUT|SSCP|[Closing the SSCP Connection](../core/closing-the-sscp-connection2.md)|  
|**Close(PLU) Request**|IN/OUT|PLU|[Closing the PLU Connection](../core/closing-the-plu-connection1.md)|  
|**Close(PLU) OK Response**|IN/OUT|PLU|[Closing the PLU Connection](../core/closing-the-plu-connection1.md)|  
|**Data-FMI**|IN/OUT|SSCP/PLU|[Data Flow](../core/data-flow1.md)|  
|**Status-Acknowledge(Ack)**|IN/OUT|SSCP/PLU|[Data Flow](../core/data-flow1.md), [Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Acknowledge(Nack-1)**|IN/OUT|SSCP/PLU|[Data Flow](../core/data-flow1.md), [Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Acknowledge(Nack-2)**|OUT|SSCP/PLU|[Inbound Data](../core/inbound-data2.md)|  
|**Status-Control(CLEAR) Request**|OUT|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(CLEAR) Ack**|IN|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(CLEAR) Nack-1**|IN|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(SDT) Request**|OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(RQR) Request**|IN|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(RQR) Ack**|OUT|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(RQR) Nack-1**|OUT|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(RQR) Nack-2**|OUT|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(STSN) Request**|OUT|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(STSN) Ack**|IN|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(STSN) Nack-1**|IN|PLU|[Recovery](../core/recovery1.md)|  
|**Status-Control(CANCEL) Request**|IN/OUT|PLU|[Outbound Chaining](../core/outbound-chaining2.md), [Inbound Chaining](../core/inbound-chaining1.md)|  
|**Status-Control(CANCEL) Ack**|IN/OUT|PLU|[Outbound Chaining](../core/outbound-chaining2.md), [Inbound Chaining](../core/inbound-chaining1.md)|  
|**Status-Control(CANCEL) Nack-1**|IN/OUT|PLU|[Outbound Chaining](../core/outbound-chaining2.md), [Inbound Chaining](../core/inbound-chaining1.md)|  
|**Status-Control(CANCEL) Nack-2**|OUT|PLU|[Inbound Chaining](../core/inbound-chaining1.md)|  
|**Status-Control(LUSTAT) Request**|IN/OUT|PLU|[LUSTATs](../core/lustats]1.md)|  
|**Status-Control(LUSTAT) Ack**|IN/OUT|PLU|[LUSTATs](../core/lustats]1.md)|  
|**Status-Control(LUSTAT) Nack-1**|IN/OUT|PLU|[LUSTATs](../core/lustats]1.md)|  
|**Status-Control(LUSTAT) Nack-2**|OUT|PLU|[LUSTATs](../core/lustats]1.md)|  
|**Status-Control(SIGNAL) Request**|IN/OUT|PLU|[Direction](../core/direction1.md)|  
|**Status-Control(SIGNAL) Ack**|OUT|PLU|[Direction](../core/direction1.md)|  
|**Status-Control(SIGNAL) Nack-1**|OUT|PLU|[Direction](../core/direction1.md)|  
|**Status-Control(SIGNAL) Nack-2**|OUT|PLU|[Direction](../core/direction1.md)|  
|**Status-Control(RSHUTD) Request**|IN|PLU|[Application-Initiated Termination](../core/application-initiated-termination1.md)|  
|**Status-Control(RSHUTD) Ack**|OUT|PLU|[Application-Initiated Termination](../core/application-initiated-termination1.md)|  
|**Status-Control(RSHUTD) Nack-1**|OUT|PLU|[Application-Initiated Termination](../core/application-initiated-termination1.md)|  
|**Status-Control(RSHUTD) Nack-2**|OUT|PLU|[Application-Initiated Termination](../core/application-initiated-termination1.md)|  
|**Status-Control(BID) Request**|OUT|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(BID) Ack**|IN|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(BID) Nack-1**|IN|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(CHASE) Request**|IN/OUT|PLU|[Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Control(CHASE) Ack**|IN/OUT|PLU|[Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Control(CHASE) Nack-1**|IN/OUT|PLU|[Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Control(CHASE) Nack-2**|OUT|PLU|[Confirmation and Rejection of Data](../core/confirmation-and-rejection-of-data]1.md)|  
|**Status-Control(SHUTC) Request**|IN|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(SHUTC) Ack**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(SHUTC) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(SHUTC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(SHUTD) Request**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(RTR) Request**|IN|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(RTR) Ack**|OUT|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(RTR) Nack-1**|OUT|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(RTR) Nack-2**|OUT|PLU|[Brackets](../core/brackets1.md)|  
|**Status-Control(QC) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QC) Ack**|IN/OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QC) Nack-1**|IN/OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QEC) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QEC) Ack**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QEC) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(QEC) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(RELQ) Request**|IN/OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(RELQ) Ack**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(RELQ) Nack-1**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Control(RELQ) Nack-2**|OUT|PLU|[Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)|  
|**Status-Error**|OUT|SSCP/PLU|[Status-Error Message](../core/status-error-message1.md)|  
|**Status-Resource**|IN|PLU|[Pacing and Chunking](../core/pacing-and-chunking1.md)|  
|**Status-Session**|OUT|SSCP/PLU|[Status-Session Message](../core/status-session-message1.md), [Status-Session Codes](../core/status-session-codes1.md)|  
|**Status-RTM**|OUT|SSCP|[RTM Parameters](../core/rtm-parameters]2.md)|  
  
 The following table lists the messages that are used for LUA only.  
  
|Message|Direction|Connection|Reference|  
|-------------|---------------|----------------|---------------|  
|**Status-Acknowledge(ACKLUA)**|OUT|SSCP/PLU|[Inbound Data from LUA Applications](../core/inbound-data-from-lua-applications1.md)|  
|**Status-Control(...) ACKLUA**|OUT|PLU|[Inbound Data from LUA Applications](../core/inbound-data-from-lua-applications1.md)|  
|**Status-Control(CRV) Request**|OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(CRV) Ack**|IN|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(CRV) Nack-1**|IN|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(BIS) Request**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(BIS) Ack**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(BIS) Nack-1**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(SBI) Request**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(SBI) Ack**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
|**Status-Control(SBI) Nack-1**|IN/OUT|PLU|[Status-Control Message](../core/status-control-message1.md)|  
  
## See Also  
 [FMI Concepts](../core/fmi-concepts1.md)   
 [SSCP Connection](../core/sscp-connection1.md)   
 [PLU Connection](../core/plu-connection2.md)   
 [Data Flow](../core/data-flow1.md)   
 [Status Messages](../core/status-messages2.md)   
