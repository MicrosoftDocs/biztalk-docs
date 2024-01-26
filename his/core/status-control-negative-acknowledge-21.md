---
description: "Learn more about: Status-Control(...) Negative-Acknowledge-2"
title: "Status-Control(...) Negative-Acknowledge-21"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Status-Control(...) Negative-Acknowledge-2
The **Status-Control(...) Negative-Acknowledge-2** message flows from the node to the application. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
  
struct Status-Control(...) Negative-Acknowledge-2 {  
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
    INTEGER    sfhdr.stctlhdr.ctlnumb2;  
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
 Control qualifier ACKNEG2 (0x04).  
  
 *sfhdr.stctlhdr.ctltype*  
 Control type.  
  
 *sfhdr.stctlhdr.ctlack*  
 Reserved.  
  
 *sfhdr.stctlhdr.ctlflag1*  
 Reserved.  
  
 *sfhdr.stctlhdr.ctlflag2*  
 Reserved.  
  
 *sfhdr.stctlhdr.ctlnumb1*  
 Error code 1.  
  
 *sfhdr.stctlhdr.ctlnumb2*  
 Error code 2.  
  
 *sfhdr.stctlhdr.ctlmsgk*  
 Message key.  
  
## Remarks  
  
-   The **Status-Control() Negative-Acknowledge-2** message consists of a buffer header only. There is no buffer element.  
  
-   The message key field matches the message key in the corresponding **Status-Control** request.  
  
-   For a summary of **Status-Control** control type codes, see the table in [Status-Control Message](./status-control-message1.md).  
  
-   For a list of error codes, see [Error and Sense Codes](./error-and-sense-codes2.md).
