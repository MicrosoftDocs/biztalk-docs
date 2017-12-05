---
title: "Open(PLU) Error Confirm1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de04ad09-a3df-4bc3-81ca-f920cf5a0d70
caps.latest.revision: 3
---
# Open(PLU) Error Confirm
The **Open(PLU) Error Confirm** message flows from the node to the application. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
  
struct Open(PLU) Error Confirm {  
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
    INTEGER   ophdr.opresid;  
    INTEGER   ophdr.operr1;  
    INTEGER   ophdr.operr2;  
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
 Open qualifier CONFERR (0x05).  
  
 *ophdr.opentype*  
 Open type LUSEC (0x02).  
  
 *ophdr.appltype*  
 Application program interface type.  
  
 0x02 (function management interface (FMI) application)  
  
 *ophdr.opluno*  
 Logical unit number.  
  
 *ophdr.opresid*  
 Resource identifier.  
  
 *ophdr.operr1*  
 Error code 1.  
  
 *ophdr.operr2*  
 Error code 2.  
  
## Remarks  
  
-   The **Open(PLU) Error Confirm** message consists of a buffer header only.  
  
-   The error codes are valid. (For more information, see [Error and Sense Codes](../core/error-and-sense-codes1.md).) An **Open(PLU) Error Confirm** closes the connection.