---
title: "Status-Acknowledge(Ack)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b954fdf-ae1d-43c0-adb2-d5b39b2b1f10
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status-Acknowledge(Ack)
The **Status-Acknowledge(Ack)** message flows from the node to the application and from the application to the node, and is used with both system services control point (SSCP) and primary logical unit (PLU) connections.  
  
 The following structure shows the message format for all SSCP messages and for PLU messages flowing from the node to the application.  
  
## Syntax  
  
```  
struct Status-Acknowledge(Ack) {  
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
struct Status-Acknowledge(Ack) {  
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
 Acknowledgment type ACKPOS (0x02).  
  
 *sfhdr.stackhdr.akmsgkey*  
 Message key.  
  
 *sfhdr.stackhdr.akflags1*  
 Application flag 1.  
  
 *sfhdr.stackhdr.akflags2*  
 Application flag 2.  
  
 *sfhdr.stackhdr.aknumb1*  
 Undefined.  
  
 *sfhdr.stackhdr.aknumb2*  
 Reserved.  
  
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
  
 The message format for PLU messages flowing from the application to the node is identical to the preceding format, except that the application flag 1 and application flag 2 fields are not used. They are replaced by the following INTEGER field:  
  
 *sfhdr.stackhdr.akmsgtim*  
 Last host response time  
  
 0xFFFF - no response time measured 0x*nnnn* - last response time measured, in units of 0.1 second  
  
||||  
|-|-|-|  
|INTEGER|*sfhdr.stackhdr.akmsgtim*|Last host response time      0xFFFF - no response time       measured      0x*nnnn* - last response time       measured, in units of 0.1       second|  
  
## Remarks  
  
-   The message key and application flags reflect the message key and application flags of the data message to which this is an acknowledgment. (For more information, see the note about LUA that follows.)  
  
-   For outbound **Status-Acknowledge(Ack)** messages from the local node to the application, the SNA sequence number gives the sequence number of the inbound data message to which this is an acknowledgment. (For more information, see the note about LUA that follows.) It is normally used only by Transmission Service profile (TS profile) 4 applications.  
  
-   For inbound **Status-Acknowledge(Ack)** messages from the application to the local node, the SNA sequence number reflects the sequence number of the outbound data message to which this is an acknowledgment.  
  
-   If the host specified that response time statistics are to be maintained, the application is responsible for measuring and reporting response times to the local node, using the **akmsgtim** field of this message. (For details, see [RTM Parameters](../HIS2010/rtm-parameters]1.md) and [Response Time Monitor Data](../HIS2010/response-time-monitor-data2.md).)  
  
-   If the application is using the LUA variant of the function management interface (FMI), the transmission header (TH) and (if appropriate) response header (RH) are included in the data, and the **startd** field points to the TH. The **akmsgkey**, **akflags1**, and **akflags2** fields are undefined and should not be used. The corresponding data from the element should be used instead. The **akseqno** field is similarly undefined on messages from the local node to the application. It must be set on messages from the application to the local node. The **akseqno** field is used to hold the sequence number of the request being acknowledged. (For more information about FMI, see [FMI Concepts](../HIS2010/fmi-concepts2.md).)  
  
-   If the application is not using the LUA variant of the FMI, the message consists of a buffer header only. There is no buffer element.