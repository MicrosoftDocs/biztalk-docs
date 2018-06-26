---
title: "X.25 Definition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c7d87a6-90ac-4e17-9c46-c7fe548cd318
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# X.25 Definition
The following table shows a sample IBM 9370 VTAM definition for X.25 circuits. The X25GROUP label shows the VTAM definitions for switched virtual circuits 001 through 006.  
  
### VTAM definition for X.25 connection  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
|X25NODE|VBUILD|TYPE=PACKET|  
|PORTA00|PORT|CUADDR=(A00,A08),NETTYPE=1, CHARGACC=YES,CHARGE=NO, VCALLS=(,,001,006,,),DIALNO=31370023061 MAXOUT=7,NETLEVEL=80,PMOD=8, PLENGTH=256,PWINDOW=3,REPLYT0=3, RETRIES=7|  
|VCPA00|VCPARMS|LC=(1,6),PWINDOW=3,PLENGTH=256|  
|X25GROUP|GROUP|DIAL=YES,LNCTL=SDLC,CALL=INOUT, ISTATUS=ACTIVE|  
|L01A00A|LINE|ADDRESS=001,AUTO=001, ISTATUS=ACTIVE|  
|P01AOOA|PU|MAXLU=32|  
|L01A00B|LINE|ADDRESS=002,ISTATUS=INACTIVE, AUTO=002|  
|P01AOOB|PU|MAXLU=32|  
|L01A00C|LINE|ADDRESS=003,ISTATUS=INACTIVE, AUTO=003|  
|P01AOOC|PU|MAXLU=32|  
|L01A00D|LINE|ADDRESS=004,ISTATUS=INACTIVE, AUTO=004|  
|P01AOOD|PU|MAXLU=32|  
|L01A00E|LINE|ADDRESS=005,ISTATUS=INACTIVE, AUTO=005|  
|P01AOOE|PU|MAXLU=32|  
|L01A00F|LINE|ADDRESS=006,ISTATUS=INACTIVE, AUTO=006|  
|P01AOOF|PU|MAXLU=32|  
  
 The following table shows the sample IBM 9370 VTAM switched definition for the X25GROUP label.  
  
### VTAM switched definition for X25GROUP  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
|X25|VBUILD|TYPE=SWNET,MAXGRP=5,MAXNO=12|  
|USER01|PU|ADDR=C1,IDBLK=05D,IDNUM=00025, ANS=CONTINUE,MAXDATA=265, MAXOUT=7,MAXPATH=0,PACING=0, VPACING=0,SSCPFM=USSSCS, IRETRY=YES,USSTAB=MSUSSTAB, PUTYPE=2,DISCNT=YES,ISTATUS=ACTIVE|  
|T01A0002|LU|LOCADDR=002,DLOGMOD=D4C32792|  
|T01A0003|LU|LOCADDR=003,DLOGMOD=D4C32792|  
|T01A0004|LU|LOCADDR=004,DLOGMOD=D4C32792|  
|T01A0005|LU|LOCADDR=005,DLOGMOD=D4C32792|  
|T01A0006|LU|LOCADDR=006,DLOGMOD=LU33286S|  
  
 The following table defines key parameters for X.25.  
  
### VTAM Parameter Descriptions for X.25  
  
|                     VTAM parameter                     |        Corresponding Host Integration Server parameter         |                                                                                                                                                                                      Description                                                                                                                                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         IDBLK=                         | First three digits of Local Node ID (basic connection setting) |                                                                         A three-digit hexadecimal value that, together with IDNUM, identifies the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. The values 000 and FFF cannot be used; these values are reserved.                                                                          |
|                         IDNUM=                         |  Last five digits of Local Node ID (basic connection setting)  |                                                                                                                                      A five-digit hexadecimal value that, together with IDBLK, identifies the Host Integration Server computer.                                                                                                                                       |
|      DIALNO=<br /><br /> (in the PORT definition)      |                      Remote X.25 Address                       |                                                                           An address that identifies an X.25 system. The address consists of from 1 through 15 hexadecimal digits. If a 15-digit address is used, the final 3 digits are used for routing between stations with the same 12-digit address.                                                                            |
| MAXDATA=<br /><br /> (in the PU definition for USER01) |             Max BTU Length (advanced X.25 setting)             |                                                                                                                                                                     The maximum length of a BTU sent or received.                                                                                                                                                                     |
|                        LOCADDR=                        |                           LU Number                            | The LU local address at the PU. For independent LUs that communicate with a host, the LOCADDR parameter must be set to 0. For dependent LUs with VTAM, the LOCADDR must be at least 2. Also, for dependent LUs, the LU numbers set in the Host Integration Server computer must match the LOCADDR values on the host.<br /><br /> In Table A.4, the LU numbers range from 002 to 006. |
  
## See Also  
 [Sample Host Definitions](../core/sample-host-definitions2.md)