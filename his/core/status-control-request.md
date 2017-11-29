---
title: "Status-Control(...) Request2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 484c1529-5587-42a3-b588-02a91644e5c2
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Status-Control(...) Request
The **Status-Control(...) Request** message flows from the node to the application and from the application to the node. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
struct Status-Control(...) Request {  
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
    CHAR      sfhdr.stctlhdr.ctltype;  
    CHAR      sfhdr.stctlhdr.ctlack;  
    CHAR      sfhdr.stctlhdr.ctlflag1;  
    CHAR      sfhdr.stctlhdr.ctlflag2;  
    INTEGER   sfhdr.stctlhdr.ctlnumb1;  
    INTEGER   sfhdr.stctlhdr.ctlnumb2;  
    INTEGER   sfhdr.stctlhdr.ctlmsgk;  
};   
struct Status-Control(...) Request {  
    PTRBFELT   hdreptr->elteptr;  
    INTEGER    hdreptr->startd;  
    INTEGER    hdreptr->endd;  
    CHAR       hdreptr->trpad;  
    CHAR[268]  hdreptr->dataru;  
};   
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to buffer element (NIL if not using LUA).  
  
 *numelts*  
 Number of buffer elements (0x00 if not using LUA).  
  
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
 Control qualifier (0x01).  
  
 *sfhdr.stctlhdr.ctltype*  
 Control type.  
  
 *sfhdr.stctlhdr.ctlack*  
 Acknowledgment required indicator.  
  
 No acknowledgment required (0x00) Acknowledgment required (0x01)  
  
 *sfhdr.stctlhdr.ctlflag1*  
 Application flag 1.  
  
 *sfhdr.stctlhdr.ctlflag2*  
 Application flag 2. (For more information, see [STSN](../Topic/STSN1.md).)  
  
 *sfhdr.stctlhdr.ctlnumb1*  
 Code 1.  
  
 *sfhdr.stctlhdr.ctlnumb2*  
 Code 2.  
  
 *sfhdr.stctlhdr.ctlmsgk*  
 Message key.  
  
 **LUA only (see Remarks):**  
**Element**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element (NIL).  
  
 *hdreptr–>startd*  
 Start of data in this buffer element.  
  
 13 or 10 for second and subsequent segments of outbound segmented request/response units (RUs)  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved.  
  
 *hdreptr–>dataru*  
 Data RU.  
  
## Remarks  
  
-   If the application is using the LUA variant of the function management interface (FMI), the transmission header (TH), response header (RH), and RU are included in the data element, and the **startd** field points to the TH. The **ctlflag1** and **ctlflag2** bytes are not defined and should not be used. The appropriate values from the data should be used instead. (For more information about FMI, see [FMI Concepts](../Topic/FMI%20Concepts2.md).)  
  
-   If the application is not using the LUA variant of the function management interface (FMI), the message consists of a buffer header only. There is no buffer element.  
  
-   For a summary of **Status-Control** control type codes, see the table in [Status-Control Message](../Topic/Status-Control%20Message2.md)  
  
-   The code 1 and code 2 fields apply only for **Status-Control** LUSTAT, SIGNAL, and STSN messages.  
  
-   The application flag byte 2 is used for the **Status-Control** STSN control byte. (For more information, see [Recovery](../Topic/Recovery2.md).)