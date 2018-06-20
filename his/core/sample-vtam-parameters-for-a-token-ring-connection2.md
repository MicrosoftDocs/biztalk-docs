---
title: "Sample VTAM Parameters for a Token Ring Connection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5909ca74-6ab1-4b5e-8daf-f6721045653f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sample VTAM Parameters for a Token Ring Connection
The following is a sample of VTAM parameters that might be used for a Token Ring connection to an IBM 9370 host. The underlined values correspond to values specified in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Manager.  

```  
R01100   PORT  
CUADDR=100,<U>MACADDR=400040004001</U>,LANCON=(5,2),X  

MAXDATA=2012,MAXSTN=52,SAPADDR=04  

SERVER01 PU     ADDR=C1, <U>IDBLK=05D, IDNUM=00001</U>,X  

ANS=CONTINUE,<U>MAXDATA=0265</U>,MAXOUT=7,MAXPATH=7,X  

PACING=0,VPACING=0,SSCPFM=USSSCS,X  

LANACK=(0,0),LANCON=(5,2),LANINACT=4.8,LANRESP=(5,2), X  

LANSDWDW=(7,1),LANSW=YES,MACADDR=400040001111,X  

USSTAB=MSUSSTAB,DLOGMOD=D4C32792,X  

PUTYPE=2,DISCNT=(NO),ISTATUS=ACTIVE,<U>SAPADDR=04</U>  

T0110002 LU   <U>LOCADDR=002</U>  
T0110003 LU   <U>LOCADDR=003</U>  
T0110004 LU   <U>LOCADDR=004</U>  
T0110005 LU   <U>LOCADDR=005</U>  
P0110006 LU   <U>LOCADDR=006</U>,DLOGMOD=LU33286S  
T0110007 LU   <U>LOCADDR=007</U>  
T0110008 LU   <U>LOCADDR=008</U>  

```  

 The following table shows the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters and values that correspond to the sample VTAM parameters.  


|        Host Integration Server parameter         | Sample value |                             VTAM parameter                             |
|--------------------------------------------------|--------------|------------------------------------------------------------------------|
|              Remote Network Address              | 400040004001 |               MACADDR= parameter in the PORT definition                |
| Local Node ID, first three digits (block number) |     05D      |         IDBLK<strong>=</strong> parameter in the PU definition         |
|  Local Node ID, last five digits (node number)   |    00001     |         IDNUM<strong>=</strong> parameter in the PU definition         |
|                  Max BTU Length                  |     265      | MAXDATA= parameter in the PU definition (set Max BTU Length ≤ MAXDATA) |
|                Remote SAP Address                |      04      |                SAPADDR= parameter in the PU definition                 |
|                    LU Numbers                    | 2 through 8  |                LOCADDR= parameter in the LU definitions                |

## Sample VTAM Parameters for an SDLC Connection  
 The following is a sample of VTAM parameters that might be used for a Synchronous Data Link Control (SDLC) connection to a host. The underlined values correspond to values specified in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Manager.  

```  
SERVER02 PU    <U>ADDR=C1,IDBLK=017,IDNUM=B8001</U>,DISCNT=NO,X  
               VPACING=00,PACING=00,PUTYPE=2,<U>MAXDATA=265</U>,X  
               DLOGMOD=D4C32792,USSTAB=MSUSSTAB  

T01B8002 LU   <U>LOCADDR=002</U>  
T01B8003 LU   <U>LOCADDR=003</U>  
T01B8004 LU   <U>LOCADDR=004</U>  
T01B8005 LU   <U>LOCADDR=005</U>  
P01B8006 LU   <U>LOCADDR=006</U>,DLOGMOD=LU33286S  

```  

 The following table shows the Host Integration Server parameters and values that correspond to the sample VTAM parameters.  


|        Host Integration Server parameter         |                Sample value                 |                             VTAM parameter                             |
|--------------------------------------------------|---------------------------------------------|------------------------------------------------------------------------|
|                Local Poll Address                |                     C1                      |                  ADDR= parameter in the PU definition                  |
| Local Node ID, first three digits (block number) |                     017                     |         IDBLK<strong>=</strong> parameter in the PU definition         |
|  Local Node ID, last five digits (node number)   |                    B8001                    |         IDNUM<strong>=</strong> parameter in the PU definition         |
|                  Max BTU Length                  |                     265                     | MAXDATA= parameter in the PU definition (set Max BTU Length ≤ MAXDATA) |
|      The encoding scheme (NRZ versus NRZI)       | Not specified; defaults to NRZI=YES on host |             The NRZI= setting in the LINE/GROUP definition             |
|                    LU Numbers                    |                 2 through 6                 |                LOCADDR= parameter in the LU definitions                |

## Sample VTAM Parameters for an X.25 Connection  
 The following is a sample of VTAM parameters that might be used for an X.25 connection to a host. The underlined values correspond to values specified in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Manager.  

```  
PORTA00  PORT  
CUADDR=(A00,A08),NETTYPE=1,CHARGACC=YES,CHARGE=NO,X  

VCALLS=(,,001,006,,),<U>DIALNO=31370023061</U>,MAXOUT=7,  
NETLEVEL=80,PMOD=8,PLENGTH=256,PWINDOW=3,  
REPLYT0=3,RETRIES=7  

SERVER03 PU  
ADDR=C1,<U>IDBLK=05D</U>,<U>IDNUM=00025</U>,ANS=CONTINUE,X  
<U>MAXDATA=265</U>,MAXOUT=7,MAXPATH=0,PACING=0,VPACING=0,X  

SSCPFM=USSSCS,IRETRY=YES,USSTAB=MSUSSTAB,PUTYPE=2,X  

DISCNT=YES,ISTATUS=ACTIVE  

```  

 The following table shows the Host Integration Server parameters and values that correspond to the sample VTAM parameters.  

|Host Integration Server parameter|Sample value|VTAM parameter|  
|---------------------------------------|------------------|--------------------|  
|Remote X.25 Address|31370023061|DIALNO= parameter in the PORT definition|  
|Local Node ID, first three digits (block number)|05D|IDBLK=parameter in the PU definition|  
|Local Node ID, last five digits (node number)|00025|IDNUM=parameter in the PU definition|  
|Max BTU Length|265|MAXDATA= parameter in the PU definition (set Max BTU Length ≤ MAXDATA)|  

## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)