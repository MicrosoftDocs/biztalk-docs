---
title: "Open(PLU) Request2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d4f77a6-b173-48ca-8c68-605cb202201a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Open(PLU) Request
The **Open(PLU) Request** message flows from the node to the application. It is used with a primary logical unit (PLU) connection.  
  
```  
struct Open(PLU) Request {  
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
    INTEGER   ophdr.icreditr;  
    INTEGER   ophdr.icredits;  
    CHAR      ophdr.opninfo1;  
};   
struct Open(PLU) Request {  
    PTRBFELT   hdreptr->elteptr;  
    INTEGER    hdreptr->startd;  
    INTEGER    hdreptr->endd;  
    CHAR       hdreptr->trpad;  
    CHAR[268]  hdreptr->dataru;  
};   
struct Open(PLU) Request {  
    PTRBFELT  hdreptr->elteptr->elteptr;  
    INTEGER   hdreptr->elteptr->startd;  
    INTEGER   hdreptr->elteptr->endd;  
    CHAR      hdreptr->elteptr->trpad;  
    CHAR[ ]   hdreptr->elteptr->dataru;  
};   
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to first buffer element.  
  
 *numelts*  
 Number of buffer elements (0x02).  
  
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
 Open qualifier REQU (0x01).  
  
 *ophdr.opentype*  
 Open type LUSEC (0x02).  
  
 *ophdr.appltype*  
 Application program interface type.  
  
 0x02 (FMI application)  
  
 *ophdr.opluno*  
 Logical unit number.  
  
 *ophdr.opresid*  
 Resource identifier.  
  
 *ophdr.icreditr*  
 Initial credit for flow from application to local node: zero (no flow control).  
  
 *ophdr.icredits*  
 Recommended initial credit for flow from local node to application: Pacing window + 1.  
  
 *ophdr.opninfo1*  
 Negotiable bind indicator.  
  
 Bind is not negotiable  (0x00)  
  
 Bind is negotiable        (0x01)  
  
 **Element 1**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element.  
  
 *hdreptr–>startd*  
 Start of data in this buffer element (1).  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved.  
  
 *hdreptr–>dataru*  
 Data RU, as follows:  
  
 dataru[0–9]  
  
 Source name.  
  
 dataru[10–19]  
  
 Destination name.  
  
 dataru[20]  
  
 Secondary pacing send window.  
  
 dataru[21]  
  
 Secondary pacing receive window.  
  
 dataru[22–23]  
  
 Secondary send maximum request/response unit (RU) size. (For more information, see Remarks.)  
  
 dataru[24–25]  
  
 Primary send maximum RU size. (For more information, see Remarks.)  
  
 dataru[26]  
  
 Secondary send chunk size (in units of elements).  
  
 dataru[27]  
  
 Primary send chunk size (in units of elements).  
  
 **Element 2**  
  
 *hdreptr–>elteptr–>elteptr*  
 Pointer to buffer element (NIL).  
  
 *hdreptr–>elteptr–>startd*  
 Start of data in this buffer element (13).  
  
 *hdreptr–>elteptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>elteptr–>trpad*  
 Reserved.  
  
 *hdreptr–>elteptr–>dataru*  
 Data RU, as follows:  
  
 dataru[13]  
  
 The **BIND** RU received from the host.  
  
## Remarks  
  
-   The **Open(PLU) Request** message consists of a buffer header, an initial element containing the source and destination names, RU sizes, and so on, followed by a second element containing the **BIND** RU received from the host.  
  
-   The source Locality Partner Index (LPI) and the L and P parts of the destination LPI are valid, but the I part of the destination LPI is reserved.  
  
-   The two send maximum RU size fields (in **dataru[22–25]**) are both integer values.  
  
-   The **BIND** RU can be up to 256 bytes in length.  
  
-   If the application is using the logical unit application (LUA) variant of the function management interface (FMI), the **BIND** RU is preceded by its transmission header (TH) and response header (RH). The **startd** field of the second element points to the TH. (For more information about FMI, see [FMI Concepts](../core/fmi-concepts2.md).)  
  
-   The LU number matches that allocated to the named application on the [Open(SSCP) Response](../core/open-sscp-response1.md).  
  
-   The resource identifier matches the value used by the application on the [Open(SSCP) Request](../core/open-sscp-request2.md).  
  
-   If chunking was specified on the **Open(SSCP) Request**, the **icredits** (initial credit from local node to application) field specifies the number of chunks, rather than RUs, that can be transmitted. The two send chunk size parameters are specified in units of elements. (Each element contains up to 256 bytes of RU data.) A value of zero indicates that the chunk size is not the limiting factor in determining the size of messages. The limiting factor is the RU size or the segment size, so chunking is not required. In this case, credit will still be used, with the unit of credit being a message.  
  
-   The **icreditr** (initial credit from application to local node) field is not used and must be set to zero.