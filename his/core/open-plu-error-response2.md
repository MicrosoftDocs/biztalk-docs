---
title: "Open(PLU) Error Response2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37a047e2-666a-4557-95f4-44312210f8fa
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Open(PLU) Error Response
The **Open(PLU) Error Response** message flows from the application to the node. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
  
struct Open(PLU) Error Response {  
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
    CHAR      ophdr.openqual;  
    CHAR      ophdr.opentype;  
    CHAR      ophdr.appltype;  
    CHAR      ophdr.opluno;  
    INTEGER  ophdr.opresid;  
    INTEGER  ophdr.operr1;  
    INTEGER  ophdr.operr2;  
};   
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to first buffer element (NIL).  
  
 *numelts*  
 Number of buffer elements (0x00).  
  
 *msgtype*  
 Message type OPENMSG (0x01).  
  
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
  
 *ophdr.openqual*  
 Open qualifier RSPERR (0x03).  
  
 *ophdr.opentype*  
 Open type LUSEC (0x02).  
  
 *ophdr.appltype*  
 Application program interface type.  
  
 0x02 (FMI application)  
  
 *ophdr.opluno*  
 Logical unit number.  
  
 *ophdr.opresid*  
 Resource identifier.  
  
 *ophdr.operr1*  
 Error code 1.  
  
 *ophdr.operr2*  
 Error code 2.  
  
## Remarks  
  
-   The **Open(PLU) Error Response** message consists of a buffer header only.  
  
-   The application should reflect the source and destination Locality Partner Index (LPIs).