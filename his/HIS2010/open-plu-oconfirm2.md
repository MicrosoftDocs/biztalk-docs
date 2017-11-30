---
title: "Open(PLU) OConfirm2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 754df9c2-7934-4c41-bd3a-11fa746a6e21
caps.latest.revision: 3
---
# Open(PLU) OConfirm
The **Open(PLU) OK Confirm** message flows from the node to the application. It is used with a primary logical unit (PLU) connection.  
  
## Syntax  
  
```  
struct Open(PLU) OK Confirm {  
    PTRBFHDR  nxtqptr;  
    PTRBFELT  hdreptr;  
    CHAR      numelts;  
    CHAR      msgtype;  
    CHAR      srcl;  
    CHAR      srcp;  
    INTEGER   srci;  
    CHAR      destl;  
    CHAR      destp;  
    INTEGER   dsti;  
    CHAR      ophdr.openqual;  
    CHAR      ophdr.opentype;  
    CHAR      ophdr.appltype;  
    CHAR      ophdr.opluno;  
    INTEGER   ophdr.opresid;  
    INTEGER   ophdr.icreditr;  
    INTEGER   ophdr.icredits;  
    CHAR      ophdr.opninfo1;  
};   
struct Open(PLU) OK Confirm {  
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
  
 *dsti*  
 Destination index.  
  
 *ophdr.openqual*  
 Open qualifier CONFOK (0x04).  
  
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
 Reserved.  
  
 *ophdr.icredits*  
 Reserved.  
  
 *ophdr.opninfo1*  
 PLU address.  
  
 **Element**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element (NIL).  
  
 *hdreptr–>startd*  
 Start of data in this buffer element (1).  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved.  
  
 *hdreptr–>dataru*  
 Data request/response unit (RU), as follows:  
  
 dataru[0]  
  
 Function management (FM) profile.  
  
 dataru[1]  
  
 Transmission Service profile (TS profile).  
  
 dataru[2]  
  
 Primary chaining use.  
  
 dataru[3]  
  
 Primary request control mode.  
  
 dataru[4]  
  
 Primary chain response protocol.  
  
 dataru[5]  
  
 Primary two-phase commit.  
  
 dataru[6]  
  
 Primary compression indicator.  
  
 dataru[7]  
  
 Primary send end bracket (EB) indicator.  
  
 dataru[8]  
  
 Secondary chaining use.  
  
 dataru[9]  
  
 Secondary request control mode.  
  
 dataru[10]  
  
 Secondary chain response protocol.  
  
 dataru[11]  
  
 Secondary two-phase commit.  
  
 dataru[12]  
  
 Secondary compression indicator.  
  
 dataru[13]  
  
 Secondary send EB indicator.  
  
 dataru[14]  
  
 Function Management Header (FMH) usage.  
  
 dataru[15]  
  
 Bracket usage.  
  
 Brackets not used (0x00)  
  
 Brackets used      (0x01)  
  
 dataru[16]  
  
 Bracket reset state.  
  
 Bracket reset state between-brackets (BETB)  (0x01)  
  
 Bracket reset state in-bracket (INB)               (0x02)  
  
 dataru[17]  
  
 Bracket termination rule.  
  
 dataru[18]  
  
 Alternate code set indicator.  
  
 dataru[19]  
  
 Sequence number availability.  
  
 dataru[20]  
  
 Normal-flow send/receive mode.  
  
 dataru[21]  
  
 Half-duplex flip-flop reset.  
  
 dataru[22]  
  
 Secondary pacing send window.  
  
 dataru[23]  
  
 Secondary pacing receive window.  
  
 dataru[24–25]  
  
 Secondary send maximum RU size (INTEGER value).  
  
 dataru[26–27]  
  
 Primary send maximum RU size (INTEGER value).  
  
 dataru[28]  
  
 LU-LU session type.  
  
 dataru[29]  
  
 PLU name size.  
  
 dataru[30–37]  
  
 PLU name (Extended Binary Coded Decimal Interchange Code or EBCDIC).  
  
 dataru[38]  
  
 Session type 1: PS Function Management Header (FMH) type.  
  
 dataru[39]  
  
 PS data stream profile.  
  
 dataru[40]  
  
 Number of outstanding destinations.  
  
 dataru[41]  
  
 Compacted data indicator.  
  
 dataru[42]  
  
 Peripheral Data Interchange Record (PDIR) allowed indicator.  
  
 dataru[43]  
  
 Session type 2 or 3: query support.  
  
 dataru[44]  
  
 Dynamic screen size.  
  
 dataru[45]  
  
 Basic row size.  
  
 dataru[46]  
  
 Basic column size.  
  
 dataru[47]  
  
 Alternate row size.  
  
 dataru[48]  
  
 Alternate column size.  
  
## Remarks  
  
-   The **Open(PLU) OK Confirm** message consists of a buffer header and one element.  
  
-   The message does not carry source and destination names. Both LPIs are valid.  
  
-   The contents of **dataru** are referred to in the text as the PLU bind information control block (BICB). The BICB is only valid for an open-qualifier of CONFOK. For further information about the contents of the BICB, see [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md).