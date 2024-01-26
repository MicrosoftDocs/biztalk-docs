---
description: "Learn more about: Errors (CPI-C)"
title: "Errors (CPI-C)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Errors (CPI-C)
The following table summarizes state changes that occur when a data transmission error is encountered.  
  
|*return_code*|Old state|New state|  
|--------------------|---------------|---------------|  
|CM_PROGRAM_ERROR_PURGING|RECEIVE|No change|  
|CM_PROGRAM_ERROR_NO_TRUNC|RECEIVE|No change|  
|CM_SVC_ERROR_PURGING|SEND|RECEIVE|  
|CM_SVC_ERROR_NO_TRUNC|SEND_PENDING|RECEIVE|  
  
 If the partner program truncates a logical record, the local program receives notification of the truncation through *return_code* on the next **Receive** call.  
  
 If a program issues **Receive** with *requested_length* set to zero, the call is executed as usual. However, *data_received* and *status_received* are not set on the same **Receive** call. (One exception to this situation is the null record sent over a mapped conversation, described in the next paragraph.)  
  
 In a mapped conversation in which data is available from the partner program, *data_received* is set to CM_INCOMPLETE_DATA_RECEIVED. If a null record is available (*send_length* in the [Send_Data](../core/send-data-cpi-c-2.md) call issued by the partner program is set to zero), *data_received* is set to CM_COMPLETE_RECORD_RECEIVED with *received_length* set to zero.  
  
 In a basic conversation in which data is available and the fill characteristic is set to CM_FILL_LL, *data_received* is set to CM_INCOMPLETE_DATA_RECEIVED. If the fill characteristic is set to CM_FILL_BUFFER, *data_received* is set to CM_DATA_RECEIVED.  
  
 The logical unit (LU) does not automatically perform any conversion between EBCDIC and ASCII on the received string of data before putting it in *buffer*. If necessary, the program can use the Common Service Verb (CSV) [CONVERT](../core/convert2.md) to translate a string from one character set to the other.
