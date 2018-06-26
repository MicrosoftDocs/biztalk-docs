---
title: "SDLC Definition (for Switched and Leased Lines)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66650eec-9ad6-4873-890e-4bddad1a51ee
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SDLC Definition (for Switched and Leased Lines)
The following table shows a sample IBM 9370 VTAM definition for four Synchronous Data Link Control (SDLC) lines. The LLGROUP label shows the VTAM definitions for lines B80 and BB0 of a leased group. The SNAGROUP label shows the VTAM definitions for lines B90 and BA0 of a switched group.  
  
### VTAM definition for four SDLC lines  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
|IBMLINE|VBUILD|TYPE=CA|  
|LLGROUP|GROUP|LNCTL=SDLC,DIAL=NO,ACTIVTO=10|  
|L01B80|LINE|ADDRESS=B80,PAUSE=0.4,REPLYTO=2.0, RETRIES=7|  
|P01B80A|PU|ADDR=C1,DISCNT=NO,PASSLIM=7, PUTYPE=2,MAXOUT=7,USSTAB=AUSSTAB|  
|T01B8002|LU|LOCADDR=002,DLOGMOD=D4C32792|  
|T01B8003|LU|LOCADDR=003,DLOGMOD=D4C32792|  
|T01B8004|LU|LOCADDR=004,DLOGMOD=D4C32792|  
|L01BB0|LINE|ADDRESS=BB0,PAUSE=0.4,REPLYTO=2.0, RETRIES=7|  
|P01BB0A|PU|ADDR=C1,DISCNT=NO,PASSLIM=7, PUTYPE=2,MAXOUT=7,USSTAB=AUSSTAB|  
|T01BB000|LU|LOCADDR=002,DLOGMOD=D4C32792|  
|T01BB001|LU|LOCADDR=003,DLOGMOD=D4C32792|  
|T01BB002|LU|LOCADDR=004,DLOGMOD=D4C32792|  
|T01BB003|LU|LOCADDR=005,DLOGMOD=D3C32792|  
|T01BB004|LU|LOCADDR=006,DLOGMOD=LU33286S|  
|SNAGROUP|GROUP|LNCTL=SDLC,DIAL=YES,MAXLU=20|  
|L01B90|LINE|ADDRESS=B90,PAUSE=0.4,REPLYTO=2.0, RETRIES=7|  
|P01B90A|PU||  
|L01BA0|LINE|ADDRESS=BA0,PAUSE=0.4,REPLYTO=2.0, RETRIES=7|  
|P01BA0A|PU||  
  
 The following table shows the sample IBM 9370 VTAM switched definition for the SNAGROUP label.  
  
### VTAM switched definition for SNAGROUP  
  
|Label|Operation|Operands|  
|-----------|---------------|--------------|  
|SWNODE|VBUILD|TYPE=SWNET,MAXGRP=0,MAXNO=0|  
|SWPU1|PU|ADDR=C1,IDBLK=017,IDNUM=DC006, DISCNT=NO,PASSLIM=2,PUTYPE=2, MAXDATA=265,MAXOUT=2, USSTAB=MSUSSTAB|  
|T01BA000|LU|LOCADDR=2,DLOGMOD=D4C32782|  
|T01BA001|LU|LOCADDR=3,DLOGMOD=D4C32782|  
|T01BA002|LU|LOCADDR=4,DLOGMOD=D4C32782|  
|T01BA003|LU|LOCADDR=5,DLOGMOD=D4C32782|  
|T01BA004|LU|LOCADDR=6,DLOGMOD=LU33286S|  
  
 The following table describes key parameters for SDLC.  
  
### VTAM Parameter Descriptions for SDLC  
  
|                    VTAM parameter                     |         Corresponding Host Integration Server parameter          |                                                                                                                                                                                   Description                                                                                                                                                                                   |
|-------------------------------------------------------|------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         ADDR=                         |               Poll Address (advanced SDLC setting)               |                                                                                                                                           A two-digit hexadecimal value that identifies the control unit that the host uses to poll.                                                                                                                                            |
|                        IDBLK=                         |  First three digits of Local Node ID (basic connection setting)  |                                                                      A three-digit hexadecimal value that, together with IDNUM, identifies the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer. The values 000 and FFF cannot be used; these values are reserved.                                                                       |
|                        IDNUM=                         |   Last five digits of Local Node ID (basic connection setting)   |                                                                                                        A five-digit hexadecimal value that, together with IDBLK, identifies the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer.                                                                                                        |
| MAXDATA=<br /><br /> (in the PU definition for SWPU1) | Max basic transmission unit (BTU) Length (advanced SDLC setting) |                                                                                                                                                 The maximum length of a BTU sent or received; BTUs are also known as I-frames.                                                                                                                                                  |
|                       LOCADDR=                        |                            LU Number                             | The LU local address at the PU. For independent LUs that communicate with a host, the LOCADDR parameter must be set to zero. For dependent LUs with VTAM, the LOCADDR must be at least 2. Also, for dependent LUs, the LU Numbers set in the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer must match the LOCADDR values on the host. |
  
 The DLOGMOD values shown in the example are the logon mode table entries from the mode table. For a complete listing of default mode table entries, see the documentation for your IBM product.  
  
## See Also  
 [Sample Host Definitions](../core/sample-host-definitions2.md)