---
title: "Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3cb6d5a-2bce-47d8-a44f-5700d7586800
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data
**Data** messages carry both inbound and outbound data between the application and the local node on all connections. For a detailed description of outbound and inbound data flows, see [Data Flow](./data-flow1.md).  
  
 The **Data** message flows from the node to the application and from the application to the node. It is used with both the system services control point (SSCP) and the primary logical unit (PLU) connections.  
  
## Syntax  
  
```  
struct Data {  
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
    CHAR      dfhdr.fhackrqd;  
    CHAR      dfhdr.fhpad1;  
    INTEGER   dfhdr.fhmsgkey;  
    CHAR      dfhdr.fhflags1;  
    CHAR      dfhdr.fhflags2;  
    INTEGER   dfhdr.fhpad2;  
    INTEGER   dfhdr.fhpad3;  
    INTEGER   dfhdr.fhseqno;  
};   
struct Data {  
    PTRBFELT   hdreptr->elteptr   
    INTEGER    hdreptr->startd   
    INTEGER    hdreptr->endd   
    CHAR       hdreptr->trpad;   
    CHAR[268]  hdreptr->dataru;  
};   
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to buffer element.  
  
 *numelts*  
 Number of buffer elements.  
  
 *msgtype*  
 Message type DATAFMI (0x20).  
  
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
  
 *dfhdr.fhackrqd*  
 Acknowledgment required indicator.  
  
 NOACKREQ    (0x00) ACKREQ         (0x01)  
  
 *dfhdr.fhpad1*  
 Reserved.  
  
 *dfhdr.fhmsgkey*  
 Message key.  
  
 *dfhdr.fhflags1*  
 Application flag 1.  
  
 *dfhdr.fhflags2*  
 Application flag 2.  
  
 *dfhdr.fhpad2*  
 Reserved.  
  
 *dfhdr.fhpad3*  
 Reserved.  
  
 *dfhdr.fhseqno*  
 Sequence number.  
  
 **Element**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element.  
  
 *hdreptr–>startd*  
 Start of data in this buffer element:  
  
 Non-logical unit application (LUA): 13, or 10 for second and subsequent segments of outbound segmented request/response units (RUs). LUA, inbound data: 4 in first element, 13 in subsequent elements.  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved.  
  
 *hdreptr–>dataru*  
 Data RU.  
  
## Remarks  
  
-   The use of the acknowledgment required indicator in both inbound and outbound data acknowledgment protocols is described in [Data Flow](./data-flow1.md).  
  
-   The use of the application flag fields is described in [Application Flags](./application-flags1.md) (For more information, see the note that follows for LUA.)  
  
-   The sequence number is undefined for inbound data but contains the corresponding SNA sequence number for outbound data.  
  
-   If the application is using the LUA variant of the function management interface (FMI), the transmission header (TH) and (if appropriate) response header (RH) are included in the data, and the **startd** field points to the TH. The **fhmsgkey**, **fhflags1**, **fhflags2**, and **fhseqno** fields are undefined and should not be used. The corresponding data from the element should be used instead. (For more information about FMI, see [FMI Concepts](./fmi-concepts1.md).)