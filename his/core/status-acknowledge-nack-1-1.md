---
title: "Status-Acknowledge(Nack-1)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 510b2e1d-4ea0-472c-a08d-9823a560e38e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status-Acknowledge(Nack-1)
The **Status-Acknowledge(Nack-1)** message flows from the node to the application and from the application to the node. It is used with both system services control point (SSCP) and primary logical unit (PLU) connections.  
  
## Syntax  
  
```  
  
struct Status-Acknowledge(Nack-1) {  
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
    CHAR      sfhdr.stackhdr.akstat;  
    CHAR      sfhdr.stackhdr.akqual;  
    INTEGER   sfhdr.stackhdr.akmsgkey;  
    CHAR      sfhdr.stackhdr.akflags1;  
    CHAR      sfhdr.stackhdr.akflags2;  
    INTEGER   sfhdr.stackhdr.aknumb1;  
    INTEGER   sfhdr.stackhdr.aknumb2;  
    INTEGER   sfhdr.stackhdr.akseqno;  
};   
struct Status-Acknowledge(Nack-1) {  
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
  
 *sfhdr.stackhdr.akstat*  
 Status type ACK (0x01).  
  
 *sfhdr.stackhdr.akqual*  
 Acknowledgment type ACKNEG1 (0x03).  
  
 *sfhdr.stackhdr.akmsgkey*  
 Message key.  
  
 *sfhdr.stackhdr.akflags1*  
 Application flag 1.  
  
 *sfhdr.stackhdr.akflags2*  
 Application flag 2.  
  
 *sfhdr.stackhdr.aknumb1*  
 Sense data 1.  
  
 *sfhdr.stackhdr.aknumb2*  
 Sense data 2.  
  
 *sfhdr.stackhdr.akseqno*  
 SNA sequence number.  
  
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
  
-   The message key and application flags reflect the message key and application flags of the data message to which this is a negative acknowledgment. (For more information, see the note about LUA that follows.)  
  
-   For **Status-Acknowledge(Nack-1)** messages from the local node to the application, the sense data reflects the sense data in the SNA negative response.  
  
-   For **Status-Acknowledge(Nack-1)** messages from the application to the local node, the sense data fields are those intended for the SNA negative response to the host.  
  
-   For outbound **Status-Acknowledge(Nack-1)** messages from the local node to the application, the SNA sequence number gives the sequence number of the inbound data message to which this is a negative acknowledgment. (For more information, see the note about LUA that follows.)  
  
-   For inbound **Status-Acknowledge(Nack-1)** messages from the application to the local node, the SNA sequence number reflects the sequence number of the outbound data message to which this is a negative acknowledgment.  
  
-   If the application is using the LUA variant of the function management interface (FMI), the transmission header (TH) and (if appropriate) response header (RH) are included in the data, and the **startd** field points to the TH. The **akmsgkey**, **akflags1**, and **akflags2** fields are undefined and should not be used. The corresponding data from the element should be used instead. The **akseqno** field is similarly undefined on messages from the local node to the application. It must be set on messages from the application to the local node. (For more information about FMI, see [FMI Concepts](./fmi-concepts1.md).)  
  
-   If the application is not using the LUA variant of the FMI, the message consists of a buffer header only. There is no buffer element.