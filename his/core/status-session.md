---
title: "Status-Session2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 427736b0-dc9a-4c2c-a97b-9328cdaae4ba
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Status-Session
The **Status-Session** message provides the application with information about changes in the state of a session between the local node and the host. It flows from the node to the application and is used with both system services control point (SSCP) and primary logical unit (PLU) connections.  
  
 For further details, see [Status-Session Message](../core/status-session-message.md).  
  
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
  
-   The session codes are listed in [Status-Session Codes](../Topic/Status-Session%20Codes2.md).