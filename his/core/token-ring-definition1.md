---
title: "Token Ring Definition1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a69fc542-6c4c-478e-8c9e-ad5d157dc9fb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Token Ring Definition
The following table shows a VTAM definition for a connection between a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer and an IBM 9370 host computer across a Token Ring local area network (LAN).  
  
### VTAM Token Ring definitions  
  
|Name|Description|Parameters|  
|----------|-----------------|----------------|  
|LANODE|VBUILD|TYPE=LAN|  
|R01100|PORT|CUADDR=100,MACADDR=400001701100, LANCON=(5,2),MAXDATA=2012, MAXSTN=32,SAPADDR=04|  
|G01100|GROUP|DIAL=YES,ISTATUS=ACTIVE,LNCTL=SDLC|  
|L01100A|LINE|CALL=INOUT|  
|P01100A|PU|MAXLU=254|  
|L01100B|LINE|CALL=INOUT|  
|P01100B|PU|MAXLU=254|  
|SWLAN|VBUILD|TYPE= SWNET,MAXGRP=5,MAXNO=12|  
|SERVER01|PU|ADDR=C1,IDBLK=05D,IDNUM=00001, ANS=CONTINUE,MAXDATA=265, MAXOUT=7,MAXPATH=7,PACING=0, VPACING=0,SSCPFM=USSSCS, LANACK=(0,0),LANCON=(5,2), LANINACT=4.8,LANRESP=(5,2), LANSDWDW=(7,1),LANSW=YES, MACADDR=4000000000FD,PUTYPE=2, DISCNT=(NO),ISTATUS=ACTIVE, SAPADDR=04|  
|E01100A|PATH|DIALNO=0004400001701100, GRPNM=G01100,GID=1,PID=1,USE=YES|  
|T0110000|LU|LOCADDR=002,DLOGMOD=D4C32782|  
|T0110001|LU|LOCADDR=003,DLOGMOD=D4C32782|  
|T0110002|LU|LOCADDR=004,DLOGMOD=D4C32782|  
|T0110003|LU|LOCADDR=005,DLOGMOD=D4C32782|  
|T0110004|LU|LOCADDR=006,DLOGMOD=LU33286S|  
  
 The following table defines key parameters for Token Ring.  
  
### VTAM parameter descriptions for Token Ring  
  
|                      VTAM parameter                      |          Corresponding Host Integration Server parameter           |                                                                                                                                                                                         Description                                                                                                                                                                                          |
|----------------------------------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                          IDBLK=                          |   First three digits of local node ID (basic connection setting)   |                                                                             A three-digit hexadecimal value that, together with IDNUM, identifies the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. The values 000 and FFF cannot be used; these values are reserved.                                                                             |
|                          IDNUM=                          |    Last five digits of local node ID (basic connection setting)    |                                                                                                              A five-digit hexadecimal value that, together with IDBLK, identifies the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer.                                                                                                               |
| MAXDATA=<br /><br /> (in the PU definition for SERVER01) | Max basic transmission unit (BTU) Length (advanced 802.2 setting)  |                                                                                                                            The maximum length of a BTU sent or received; BTUs are also known as I-frames. Max BTU Length should be less than or equal to MAXDATA.                                                                                                                            |
|      MACADDR=<br /><br /> (in the PORT definition)       |            Remote Network Address (basic 802.2 setting)            |                                                                                                                                                              The media access control address, a 12-digit hexadecimal address.                                                                                                                                                               |
|       SAPADDR=<br /><br /> (in the PU definition)        | Remote service access point (SAP) Address (advanced 802.2 setting) |                                                                                                                                             The system access point address, a two-digit hexadecimal number, a multiple of 4, between 04 and EC.                                                                                                                                             |
|       LOCADDR=<br /><br /> (in the LU definition)        |                       Local unit (LU) Number                       | The LU local address at the physical unit (PU). For independent LUs that communicate with a host, the LOCADDR parameter must be set to 0. For dependent LUs with VTAM, the LOCADDR must be at least 2. Also, for dependent LUs, the LU Numbers set in the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer must match the LOCADDR values on the host. |
  
 The GRPNM value shown in the sample above is a group name; group names must match the label of a VTAM group definition. The DLOGMOD values shown in the sample are the logon mode table entries from the mode table. For descriptions of the group macros used in these samples and a complete listing of default mode table entries, see the documentation for your IBM product.  
  
## See Also  
 [Sample Host Definitions](../core/sample-host-definitions2.md)