---
title: "Status-RTM1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7e8cae9-ce48-49f7-9a1c-b2ed81a64229
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status-RTM
The **Status-RTM** message provides the application with information about the Response Time Monitor (RTM) measurement parameters used by the host. This allows the application to match its local display of RTM statistics, if it provides such a display, with the statistics used by the host. It flows from the node to the application and is used with an system services control point (SSCP) connection.  
  
 For further details, see [Response Time Monitor Data](../core/response-time-monitor-data2.md).  
  
## Syntax  
  
```  
struct Status-RTM {  
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
    CHAR      sfhdr.strtmhdr.rtmstat;  
    CHAR      sfhdr.strtmhdr.strbndry;  
    CHAR      sfhdr.strtmhdr.strcount;  
    CHAR      sfhdr.strtmhdr.strtmdef;  
    CHAR      sfhdr.strtmhdr.strtmact;  
    CHAR      sfhdr.strtmhdr.strtmdsp;  
};   
struct Status-RTM {  
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
 Pointer to buffer element.  
  
 *numelts*  
 Number of buffer elements.  
  
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
  
 *sfhdr.strtmhdr.rtmstat*  
 Status type STRTM (0x06).  
  
 *sfhdr.strtmhdr.strbndry*  
 RTM boundaries.  
  
 0x00 - No RTM boundaries follow in element. 0x01 - RTM boundaries follow in element.  
  
 *sfhdr.strtmhdr.strcount*  
 RTM counters.  
  
 0x00 - No RTM counters follow in element. 0x01 - RTM counters follow in element.  
  
 *sfhdr.strtmhdr.strtmdef*  
 RTM definition.  
  
 0x00 - No change: use last received definition. 0x01 - Timers run until first data is written to screen. 0x02 - Timers run until keyboard is unlocked. 0x03 - Timers run until application can send (change direction (CD) or end bracket (EB) received).  
  
 *sfhdr.strtmhdr.strtmact*  
 RTM measurement.  
  
 0x00 - not active 0x01 - active  
  
 *sfhdr.strtmhdr.strtmdsp*  
 Local RTM display.  
  
 0x00 - disabled 0x01 - enabled  
  
 **Element**  
  
 *hdreptr–>elteptr*  
 Pointer to buffer element (NIL).  
  
 *hdreptr–>startd*  
 Start of data in this element.  
  
 *hdreptr–>endd*  
 End of data in this element.  
  
 *hdreptr–>trpad*  
 Reserved.  
  
 *hdreptr–>dataru*  
 Data RU, as follows:  
  
 dataru[0–1]  
  
 Number of boundaries in element  
  
 0x0000 - no boundaries included  
  
 *m* - number of boundaries included  
  
 dataru[2–3]  
  
 Number of counters in element  
  
 0x0000 - no counters included  
  
 *n* - number of counters included  
  
 dataru[4–(2m+3)]  
  
 *m* boundary values.  
  
 dataru[(2m+4)–(2m+2n+3)]  
  
 *n*counter values.  
  
 dataru[(2m+2n+4)  
  
 RTM total time.  
  
## Remarks  
  
-   A **Status-RTM** message is sent after the **Open(SSCP) OK Response** to give the initial RTM parameters. It is sent again when the RTM counters are reset (either on request from the host or when the local node sends unsolicited RTM data to the host), or when the host changes any of the RTM parameters.  
  
-   The message is sent only for applications that use LUs with type video display unit (VDU) or logical units (LUs) in a VDU pool, because the RTM feature applies only to 3270 display sessions.  
  
-   All the values in the data RU are integer values.  
  
-   The RTM counter values in this message can be nonzero at startup, because RTM statistics are maintained for a specific LU and not for a specific application's use of that LU. If zero counter values are included, this indicates that the counters are to be reset.  
  
-   The RTM total time field is present only if the number of counters in the element is nonzero.