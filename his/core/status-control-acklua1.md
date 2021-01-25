---
description: "Learn more about: Status-Control(...) ACKLUA"
title: "Status-Control(...) ACKLUA1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef6b895f-4caa-4a5e-9a5a-2bc47fd37674
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Status-Control(...) ACKLUA
The **Status-Control(...) ACKLUA** message is for logical unit application (LUA) applications only. It flows from the node to the application, and is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
  
struct Status-Control(...) ACKLUA {  
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
    CHAR      sfhdr.stctlhdr.ctlstat;  
    CHAR      sfhdr.stctlhdr.ctlqual;  
    CHAR      sfhdr.stctlhdr.ctltype  
    CHAR      sfhdr.stctlhdr.ctlack;  
    CHAR      sfhdr.stctlhdr.ctlflag1;  
    CHAR      sfhdr.stctlhdr.ctlflag2;  
    INTEGER   sfhdr.stctlhdr.ctlnumb1;  
    INTEGER   sfhdr.stctlhdr.ctlnumb2;  
    INTEGER   sfhdr.stctlhdr.ctlmsgk;  
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
  
 *sfhdr.stctlhdr.ctlstat*  
 Status type STCNTRL (0x02).  
  
 *sfhdr.stctlhdr.ctlqual*  
 Control qualifier ACKLUA (0x05).  
  
 *sfhdr.stctlhdr.ctltype*  
 Control type.  
  
 *sfhdr.stctlhdr.ctlack*  
 Reserved.  
  
 *sfhdr.stctlhdr.ctlflag1*  
 Application flag 1.  
  
 *sfhdr.stctlhdr.ctlflag2*  
 Application flag 2.  
  
 *sfhdr.stctlhdr.ctlnumb1*  
 Code 1.  
  
 *sfhdr.stctlhdr.ctlnumb2*  
 Code 2.  
  
 *sfhdr.stctlhdr.ctlmsgk*  
 Message key used for the SNA sequence number. (For more information, see Remarks.)  
  
## Remarks  
  
-   The **Status-Control() ACKLUA** message consists of a buffer header only. There is no buffer element.  
  
-   The application flags and the code 1 and code 2 fields are undefined and should not be used.  
  
-   The message key field gives the sequence number from the transmission header of the inbound data message to which this is an acknowledgment.  
  
-   For a summary of **Status-Control** control type codes, see the table in [Status-Control Message](./status-control-message1.md).
