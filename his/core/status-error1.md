---
title: "Status-Error1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e33465b9-b45f-4ca7-8ef6-62e6442ee756
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status-Error
The **Status-Error** message is used to report request reject and response header (RH) usage error conditions in outbound SNA request/response units (RUs) to the application. It flows from the node to the application and is used with both system services control point (SSCP) and primary logical unit (PLU) connections.  
  
 For more information, see [Status-Error Message](./status-error-message1.md).  
  
## Syntax  
  
```  
  
struct Status-Error {  
    PTRBFHDR  nxtqptr;  
    PTRBFELT  hdreptr;  
    CHAR      numelts;  
    CHAR      msgtype;  
    CHAR      srcl;  
    CHAR      srcp;  
    INTEGER   srci;  
    CHAR      destl;  
    CHAR      destp;  
    INTEGER   desti;  
    CHAR      sfhdr.sterrhdr.errstat;  
    CHAR      sfhdr.sterrhdr.errpad1;  
    CHAR      sfhdr.sterrhdr.errpad2;  
    CHAR      sfhdr.sterrhdr.errpad3;  
    CHAR      sfhdr.sterrhdr.errcode1;  
    CHAR      sfhdr.sterrhdr.errcode2;  
};   
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to buffer element (NIL).  
  
 *numelts*  
 Number of buffer elements (0x00).  
  
 *msgtype*  
 Message type STATFMI (0x21).  
  
 *srcl*  
 Source locality.  
  
 *srcp*  
 Source partner.  
  
 *srci*  
 Source index.  
  
 *destl*  
 Destination locality.  
  
 *destp*  
 Destination partner.  
  
 *desti*  
 Destination index.  
  
 *sfhdr.sterrhdr.errstat*  
 Status type STERROR (0x03).  
  
 *sfhdr.sterrhdr.errpad1*  
 Reserved.  
  
 *sfhdr.sterrhdr.errpad2*  
 Reserved.  
  
 *sfhdr.sterrhdr.errpad3*  
 Reserved.  
  
 *sfhdr.sterrhdr.errcode1*  
 Error code 1.  
  
 *sfhdr.sterrhdr.errcode2*  
 Error code 2.  
  
## Remarks  
  
-   The **Status-Error** message consists of a buffer header only. There is no buffer element.  
  
-   The error codes are listed in [Error and Sense Codes](./error-and-sense-codes2.md).