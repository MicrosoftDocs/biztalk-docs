---
title: "Status-Acknowledge(ACKLUA)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f34ef80-2f99-455b-b9bb-666e5ba2e8c6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status-Acknowledge(ACKLUA)
The **Status-Acknowledge(ACKLUA)** message is for logical unit application (LUA) applications only. It flows from the node to the application, and is used with both the system services control point (SSCP) and primary logical unit (PLU) connections.  
  
## Syntax  
  
```  
  
struct Status-Acknowledge(ACKLUA) {  
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
    CHAR      sfhdr.stackhdr.akstat;  
    CHAR      sfhdr.stackhdr.akqual;  
    INTEGER   sfhdr.stackhdr.akmsgkey;  
    CHAR      sfhdr.stackhdr.akflags1;  
    CHAR      sfhdr.stackhdr.akflags2;  
    INTEGER   sfhdr.stackhdr.aknumb1;  
    INTEGER   sfhdr.stackhdr.aknumb2;  
    INTEGER   sfhdr.stackhdr.akseqno;  
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
  
 *sfhdr.stackhdr.akstat*  
 Status type ACK (0x01).  
  
 *sfhdr.stackhdr.akqual*  
 Acknowledgment type.  
  
 *sfhdr.stackhdr.akmsgkey*  
 Message key.  
  
 *sfhdr.stackhdr.akflags1*  
 Application flag 1.  
  
 *sfhdr.stackhdr.akflags2*  
 Application flag 2.  
  
 *sfhdr.stackhdr.aknumb1*  
 Number of replies.  
  
 *sfhdr.stackhdr.aknumb2*  
 Reserved.  
  
 *sfhdr.stackhdr.akseqno*  
 SNA sequence number.  
  
## Remarks  
  
-   The message key and application flags are undefined and should not be checked.  
  
-   The SNA sequence number gives the sequence number of the inbound data message to which this is an acknowledgment.