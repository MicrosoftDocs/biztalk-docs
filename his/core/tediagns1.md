---
description: "Learn more about: tediagns"
title: "tediagns1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# tediagns
The diagnostics record tediagns includes a number of tedalert information records.  
  
## Syntax  
  
```  
  
typedef struct tediagns {  
    USHORT   dilen;  
    USHORT   ditype;  
    UCHAR    dinetmgt[9];  
    USHORT   disrtmco;  
    USHORT   disrtmub;  
    USHORT   diwruldr;  
    USHORT   dirtmth1;  
    USHORT   dirtmth2;  
    USHORT   dirtmth3;  
    USHORT   dirtmth4;  
    TEDALERT dialerts[20];  
    UCHAR    diaudit[128];  
    UCHAR    dierror[128];  
    USHORT   diaudlev;  
    UCHAR    dipad[16];  
} TEDIAGNS;  
```  
  
## Members  
 *dilen*  
 Length of record.  
  
 *ditype*  
 Type of record.  
  
 *dinetmgt[9]*  
 Network management connection name.  
  
 *disrtmco*  
 Send Response Time Monitor (RTM) data at counter overflow.  
  
 *disrtmub*  
 Send RTM data at UNBIND.  
  
 *diwruldr*  
 The definition by which response times are to be measured. The application should measure the response time from the time the user presses ENTER or an AID key to send data to the host, until one of the following events as defined by this field:  
  
 CERTWRIT (0)  
  
 The first host data reaches the 3270 display.  
  
 CERTUNLK (1)  
  
 The host unlocks the user's keyboard.  
  
 CERTDIRE (2)  
  
 The host gives the application direction so that the user can send further data.  
  
 Note that the host can override these definitions; for more information, see [RTM Parameters](../core/rtm-parameters]2.md).  
  
 *dirtmth1*  
 The thresholds that define the bands into which response times are to be classified. Note that the host can override these definitions; for more information, see [RTM Parameters](../core/rtm-parameters]2.md).  
  
 *dirtmth2*  
 RTM threshold #2.  
  
 *dirtmth3*  
 RTM threshold #3.  
  
 *dirtmth4*  
 RTM threshold #4.  
  
 *dialerts[20]*  
 Up to 20 alert records that define the alerts that Host Integration Server users can send to a host. There are always 20 records, but some of these can be blank, indicating that they are not used. The application should display the descriptions of any nonblank alerts together with the alert number (from 1 to 20) defined by the position of the alert record in this array.  
  
 *diaudit[128]*  
 Audit log file name.  
  
 *dierror[128]*  
 Error log file name.  
  
 *diaudlev*  
 Default audit level.  
  
 *dipad[16]*  
 16 bytes of padding.
