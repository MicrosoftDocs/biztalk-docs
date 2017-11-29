---
title: "Error and Sense Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d9ff853-d599-48f9-b72d-a5b69f05d8b9
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Error and Sense Codes
This section describes the error and sense codes that are reported to the application in the following messages:  
  
-   [Error Codes for Open(SSCP) Error Response](../core/error-codes-for-open-sscp-error-response.md)  
  
-   [Error Codes for Open(PLU) Error Confirm](../core/error-codes-for-open-plu-error-confirm.md)  
  
-   [Error Codes for Nack-2 Messages](../core/error-codes-for-nack-2-messages.md)  
  
-   [Error Codes for Status-Error Messages](../core/error-codes-for-status-error-messages.md)  
  
-   [Sense Codes for SDI Messages](../core/sense-codes-for-sdi-messages.md)  
  
 Where the reported codes are SNA sense codes, a more complete description is given in Chapter 8 of the IBM document *Systems Network Architecture: Reference Summary* (GA27-3136). These SNA sense codes are also documented in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] Help.  
  
 In addition, the local node delivers negative responses from the host as **Status-Acknowledge(Nack-1)** and **Status-Control(...) Negative-Acknowledge-1**, which can have any SNA sense code.  
  
 Application designers should note that error codes listed here that are specific to Host Integration Server always have an initial byte value of 0x00, and therefore can be easily distinguished from SNA sense codes, which have nonzero initial bytes.  
  
 The error codes are listed in topics for each type of message with an indication of the reason for the error.  
  
 This section contains:  
  
-   [Error Codes for Open Messages](../core/error-codes-for-open-messages.md)  
  
-   [Error Codes for Nack-2 Messages](../core/error-codes-for-nack-2-messages.md)  
  
-   [Error Codes for Status-Error Messages](../core/error-codes-for-status-error-messages.md)  
  
-   [Sense Codes for SDI Messages](../core/sense-codes-for-sdi-messages.md)