---
description: "Learn more about: Open(SSCP) Response"
title: "Open(SSCP) Response1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1ebb6b1-4a53-4663-9fef-24827d179e6e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Open(SSCP) Response
The **Open(SSCP) Response** message flows from the node to the application. It is used with an system services control point (SSCP) connection.  
  
## Syntax  
  
```  
struct Open(SSCP) Response {  
    PTRBFHDR  nxtqptr;  
    PTRBFELT hdreptr;  
    CHAR     numelts;  
    CHAR     msgtype;  
    CHAR     srcl;  
    CHAR     srcp;  
    INTEGER  srci;  
    CHAR     destl;  
    CHAR     destp;  
    INTEGER  desti;  
    CHAR     ophdr.openqual;  
    CHAR     ophdr.opentype;  
    CHAR     ophdr.appltype;  
    CHAR     ophdr.opluno;  
    INTEGER  ophdr.opresid;  
    INTEGER  ophdr.operr1;  
    INTEGER  ophdr.operr2;  
};  
struct Open(SSCP) Response {  
    PTRBFELT  hdreptr->elteptr;  
    INTEGER   hdreptr->startd;  
    INTEGER   hdreptr->endd;  
    CHAR      hdreptr->trpad;  
    CHAR[256] dataru;  
};  
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdreptr*  
 Pointer to first buffer element.  
  
 *numelts*  
 Number of buffer elements (0x01).  
  
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
 Open qualifier.  
  
 RSPOK    (0x02) RSPERR  (0x03)  
  
 *ophdr.opentype*  
 Open type SSCPSEC (0x01).  
  
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
  
 **Element 1**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element (NIL).  
  
 *hdreptr–>startd*  
 Start of data in this buffer element (1).  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved (1 byte).  
  
 *hdreptr–>dataru*  
 Data RU, as follows:  
  
 dataru[0–9]  
  
 Source name.  
  
 dataru[10–19]  
  
 Destination name.  
  
 dataru[20–27]  
  
 Name of the local node that accepted the Open.  
  
 dataru[28–35]  
  
 Name of the connection used by the logical unit (LU).  
  
 dataru[36–37]  
  
 The internal identifier of the local node for the connection. (For more information, see Remarks.)  
  
 dataru[38]  
  
 The type of link service used by the connection, as shown in the following table.  
  
|Link service|Connection|  
|------------------|----------------|  
|CESLINK|(03) - SDLC|  
|CESX25|(04) - X.25|  
|CESTR|(11) - Token Ring|  
|CESTCPIP|(30) - TCP/IP|  
|CESRELAY|(31) - Frame Relay|  
|CESCHANL|(32) - Channel|  
|CESISDN|(33) – ISDN|  
|CESETHER|(34) - Ethernet 802.2|  
  
## Remarks  
  
-   The **Open(SSCP) Response** message consists of a buffer header and a single buffer element.  
  
-   If the open qualifier is RSPERR, the error code is valid and the Locality Partner Index (LPIs) and names are undefined. (For more information, see [Error and Sense Codes](./error-and-sense-codes2.md).)  
  
-   The LU number indicates the LU selected by the local node from the configuration data. (For more information, see [Opening the SSCP Connection](./opening-the-sscp-connection1.md).)  
  
-   When the **Open(SSCP)** is for an LU group, the source name contains the name of the selected LU.  
  
-   The connection identifier is an integer value. It uniquely identifies a particular connection on this local node. All sessions using the same connection will return the same identifier. This value is typically used when a link error is received on one session to determine which other sessions will be affected.
