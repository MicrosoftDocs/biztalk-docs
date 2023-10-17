---
description: "Learn more about: Close(SSCP) Response"
title: "Close(SSCP) Response1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc77dc21-53fd-4b50-8ee9-7148c88ef689
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Close(SSCP) Response
The **Close(SSCP) Response** message flows from the node to the application. It is used with a system services control point (SSCP) connection.  
  
## Syntax  
  
```  
struct Close(SSCP) Response {  
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
 Close qualifier RSPOK (0x02).  
  
 *clhdr.clstype*  
 Close subtype SSCPSEC (0x01).  
  
## Remarks  
  
-   The **Close(SSCP) Response** message consists of a buffer header only. There is no buffer element.  
  
-   The **Close(SSCP)** protocol is unconditional. It is not possible for the local node to keep the SSCP connection open after the application sends **Close(SSCP)**.
