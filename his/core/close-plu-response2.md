---
title: "Close(PLU) Response2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9842a61d-2312-4765-bff5-9fe8dc459908
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Close(PLU) Response
The **Close(PLU) Response** message flows from the node to the application and from the application to the node. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
  
struct Close(PLU) Response {  
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
 Close subtype LUSEC (0x02).  
  
## Remarks  
  
-   The **Close(PLU) Response** message consists of a buffer header only. There is no buffer element.  
  
-   The **Close(PLU)** protocol is unconditional. It is not possible for the recipient of a [Close(PLU) Request](../core/close-plu-request2.md) (either the local node or an application) to keep the PLU connection open. The only valid response is **Close(PLU) Response** with the close qualifier as RSPOK.