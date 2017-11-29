---
title: "Status-Resource1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b45c81ca-255f-404f-a2b9-221e7cd1413b
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Status-Resource
The **Status-Resource** message is used to provide a simple flow control mechanism between the local node and the application to prevent the application from exhausting its resources. It flows from the application to the node, and is used with a primary logical unit (PLU) connection.  
  
 It is only used on the PLU connection where the application specifies in the PLU connection information control block (CICB) that pacing requires application participation. For further details, see [Pacing and Chunking](../Topic/Pacing%20and%20Chunking2.md).  
  
## Syntax  
  
```  
  
struct Status-Resource {  
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
    CHAR      sfhdr.streshdr.resstat;  
    CHAR      sfhdr.streshdr.respad;  
    CHAR      sfhdr.streshdr.rescred;  
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
  
 *sfhdr.streshdr.resstat*  
 Status type STRESRCE (0x04).  
  
 *sfhdr.streshdr.respad*  
 Reserved.  
  
 *sfhdr.streshdr.rescred*  
 Application credit.  
  
## Remarks  
  
-   The **Status-Resource** message consists of a buffer header only. There is no buffer element.  
  
-   The **rescred** (application credit) field indicates that the application can receive further credit request/response units (RUs) of the maximum RU size, or further credit chunks if chunking is being used.