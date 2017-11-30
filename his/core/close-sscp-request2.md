---
title: "Close(SSCP) Request2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b1d0eb2-3cac-40f0-97fb-fdec4a49c7d1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Close(SSCP) Request
The **Close(SSCP) Request** message flows from the application to the node. It is used with a system services control point (SSCP) connection.  
  
## Syntax  
  
```  
struct Close(SSCP) Request {  
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
    CHAR      clhdr.closqual;  
    CHAR      clhdr.clstype;  
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
 Message type CLOSEMSG (0x02).  
  
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
  
 *clhdr.closqual*  
 Close qualifier REQU (0x01).  
  
 *clhdr.clstype*  
 Close subtype SSCPSEC (0x01).  
  
## Remarks  
  
-   The **Close(SSCP) Request** message consists of a buffer header only. There is no buffer element.