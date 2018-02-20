---
title: "VTAM definitions & TP requirements | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3be1942e-1e13-4c52-8b41-a0ffaa6e42ab
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TI VTAM definitions & TP requirements - HIS

## VTAM Definitions & TP coding requirements
Each remote system must be defined to VTAM in its table of Network Addressable Units, (NAUs), using logical unit (LU) definitions.  
  
 If a LOGAPPL parameter is specified on the LU definition naming the CICS system, CICS will attempt to establish a session to that LU whenever it becomes active. This is necessary if TPs residing in CICS do not use the **ALLOCATE** verb with RETURN_CONTROL=WHEN_SESSION_ALLOCATED to establish sessions. There must also be a VTAM mode table definition present for LU 6.2, although CICS does not use the values specified here.  
  
### Sample VTAM network control program (NCP) definition for LU 6.2  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
|TPPU62|PU|ADDR=C1,IBLK=03E,IDNUM=01A1A, IRETRY=YES,DISCNT=NO,ISTATUS=ACTIVE, MAXDATA=265,SSCPFM=USSSCS, MODETAB=MRNDS,USSTAB=USSNDN1, MAXOUT=7,PASSLIM=7,PUTYPE=2|  
|TPLU6207|LU|LOCADDR=7,DLOGMOD=LU62, USSTAB=USSNOMSG|  
|TPLU6208|LU|LOCADDR=8,DLOGMOD=LU62, USSTAB=USSNOMSG|  
|TPLU6209|LU|LOCADDR=9,DLOGMOD=LU62, USSTAB=USSNOMSG|  
|TPLU620A|LU|LOCADDR=A,DLOGMOD=LU62, USSTAB=USSNOMSG|  
  
 The following table shows NCP mode table entries for LU 6.2.  
  
### Sample NCP mode table entries for LU 6.2  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
||MODETAB||  
|LU62|MODEENT|LOGMODE=NORMAL|  
||. . .||  
||MODEEND||  
  
> [!NOTE]
>  It is recommended that the mode used by LU 6.2 be listed first, as shown by the LU62 example in the preceding table.  

## TP Coding Requirements
To work with CICS, TPs must be coded to specify a SYSID parameter on the **ALLOCATE** request that matches the defined SYSIDNT parameter configured in the DFHTCT tables. This request must be in the following format:  
  
```  
EXEC CICS ALLOCATE SYSID('DC11')  
  
```  
  
 The SYSID field must match the SYSIDNT field specified for a CICS program by the DFHTCT definition in the TCT (Terminal Control Table). The TCT then uses the NETNAME parameter to refer to a specific LU in the VTAM table of the NAUs (Network Addressable Units). This parameter is used by the TP to communicate with the remote system. 
  
## See Also  
 [CICS and VTAM Sample Definitions for LU 6.2](../core/cics-and-vtam-sample-definitions-for-lu-6-21.md)