---
description: "Learn more about: Status-Session"
title: "Status-Session2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Status-Session
The **Status-Session** message provides the application with information about changes in the state of a session between the local node and the host. It flows from the node to the application and is used with both system services control point (SSCP) and primary logical unit (PLU) connections.  
  
 For further details, see [Status-Session Message](../core/status-session-message1.md).  
  
## Syntax  
  
```  
  
struct Status-Session {  
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
    CHAR      sfhdr.stseshdr.sesstat;  
    CHAR      sfhdr.stseshdr.sesspad;  
    CHAR      sfhdr.steeshdr.sesscode;  
    CHAR      sfhdr.stseshdr.sessqual;  
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
  
 *sfhdr.stseshdr.sesstat*  
 Status type STSESSN (0x05).  
  
 *sfhdr.stseshdr.sesspad*  
 Reserved.  
  
 *sfhdr.steeshdr.sesscode*  
 Session code.  
  
 *sfhdr.stseshdr.sessqual*  
 Session code qualifier.  
  
## Remarks  
  
-   The **Status-Session** message consists of a buffer header only. There is no buffer element.  
  
-   The session codes are listed in [Status-Session Codes](./status-session-codes1.md).
