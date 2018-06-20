---
title: "Sample VTAM Parameters for Independent APPC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebd80244-834d-4625-8536-7a240f2e60d0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sample VTAM Parameters for Independent APPC
The lists in this section show sample VTAM parameters that might be used for communication using independent Advanced Program-to-Program Communications (APPC). The underlined values correspond to values specified in SNA Server Manager.  

```  
SERVER1  PU    ADDR=09,                                X  
               <U>IDBLK=05D</U>,                              X  
               <U>IDNUM=11111</U>,                            X  
               <U>CPNAME=SNASERV</U>,                         X  
               ISTATUS=ACTIVE                          X  
               DLOGMOD=D4C32782,                       X  
               MODETAB=ISTINCLM,                       X  
               <U>MAXDATA=521</U>,                            X  
               MAXPATH=1,                              X  
               PUTYPE=2,                               X  
               SSCPFN=USSSCS,                          X  
               MAXOUT=7,                               X  
               PASSLIM=4,                              X  
               PACING=0,                               X  
               DISCNT=NO,                              X  
               USSTAB=USSTAB                             

TRPATH    PATH DIALNO=2223331234567890,                X  
               GRPNM=AAA01,                            X  
               GID=2  

<U>LOCLU1</U>    LU   LOCADDR=0,                              X  
               ISTATUS=ACTIVE,<U>DLOGMOD=APPCMODE</U>,        X  
               RESSCB=25,USSTAB=USSTAB,PACING=0,       X  
               VPACING=0  

```  

 In the preceding example, the LOCADDR= value for the LOCLU1 is 0. This is the correct value to use with independent APPC LUs.  

 The following table shows [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters and values that correspond to the preceding sample VTAM parameters.  


|                Host Integration Server parameter                 | Sample value |                             VTAM parameter                             |
|------------------------------------------------------------------|--------------|------------------------------------------------------------------------|
| **Connection:** Local Node ID, first three digits (block number) |     05D      |         IDBLK<strong>=</strong> parameter in the PU definition         |
|  **Connection:** Local Node ID, last five digits (node number)   |    11111     |         IDNUM<strong>=</strong> parameter in the PU definition         |
|                  **Server:** Control Point Name                  |   SNASERV    |        CPNAME<strong>=</strong> parameter in the PU definition         |
|                  **Connection:** Max BTU Length                  |     521      | MAXDATA= parameter in the PU definition (set Max BTU Length ≤ MAXDATA) |
|                    **Local APPC LU:** LU Name                    |    LOCLU1    |                         Name in LU definition                          |
|                    **APPC Partner LUs:** Mode                    |   APPCMODE   |                DLOGMOD= parameter in the LU definition                 |

 The following list shows mode table entries for use with independent APPC LUs.  

```  
*********************************************************  
*           LOGMODE TABLE ENTRY FOR RESOURCES           *  
*          CAPABLE OF ACTING AS LU 6.2 DEVICES          *  
*********************************************************  
SNASVCMG MODEENT LOGMODE=SNASVCMG,FMPROF=X'13',         X  
               TSPROF=X'07',PRIPROT=X'B0',              X  
               SECPROT=X'B0',COMPROT=X'D0B1',           X  
               RUSIZES=X'8585',ENCR=B'0000',            X  
               PSERVIC=X'060200000000000000000300'  

<U>APPCMODE</U> MODEENT LOGMODE=APPCMODE,                      X  
               TYPE=0,                                  X  
               FMPROF=X'13',                            X  
               TSPROF=X'07',                            X  
               PRIPROT=X'B0',                           X  
               SECPROT=X'B0',                           X  
               COMPROT=X'50B1',                         X  
               PSNDPAC=X'03',                           X  
               SRCVPAC=X'03',                           X  
               RUSIZES=X'8585',                         X  
               PSERVIC=X'060200000000000000002F00'  

```  

 In the preceding list, the mode named APPCMODE is an example of a mode configured for use with APPC. The mode named SNASVCMG is included in Host Integration Server, because it is required for parallel session support; it does not need to be configured in SNA Server Manager.  

## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)