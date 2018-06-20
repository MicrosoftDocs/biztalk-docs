---
title: "Configuring VTAM for APPC Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9308d96-1df0-43fd-96a8-9b49e6938ca5
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring VTAM for APPC Access
Parameters on VTAM must match Advanced Program-to-Program Communications (APPC) parameters on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. To configure the needed parameters, consult with the host administrator for the matching VTAM parameters.  

 The following tables show Host Integration Server parameters and values that correspond to VTAM and CICS parameters. Note that the values given are samples only and may not work for your configuration.  

 The following table shows Host Integration Server parameters and values that correspond to sample VTAM parameters.  


|                Host Integration Server parameter                 | Sample value |                             VTAM parameter                             |
|------------------------------------------------------------------|--------------|------------------------------------------------------------------------|
| **Connection:** Local Node ID, first three digits (block number) |     05D      |         IDBLK<strong>=</strong> parameter in the PU definition         |
|  **Connection:** Local Node ID, last five digits (node number)   |    11111     |         IDNUM<strong>=</strong> parameter in the PU definition         |
|                  **Server:** Control Point Name                  |   SNASERV    |        CPNAME<strong>=</strong> parameter in the PU definition         |
|                  **Connection:** Max BTU Length                  |     521      | MAXDATA= parameter in the PU definition (set Max BTU Length ≤ MAXDATA) |
|                    **Local APPC LU:** LU Name                    |    LOCLU1    |                         Name in LU definition                          |
|                   **LU 6.2 Partner LUs:** Mode                   |   APPCMODE   |                DLOGMOD= parameter in the LU definition                 |

 The mode named APPCMODE is an example of a mode configured for use with LU 6.2. The mode named SNASVCMG is included in Host Integration Server, because it is required for parallel session support. It does not need to be configured.  

 The following table shows Host Integration Server parameters and values that correspond to sample CICS parameters.  

|Host Integration Server parameter|Sample value|CICS parameter|  
|---------------------------------------|------------------|--------------------|  
|LU Name for Local APPC LU|LOCLU1|Sessions|  
|Mode name|APPCMODE|Modename|  
|Parallel Session Limit in the mode|250|Maximum|  
|Partner Min Contention Winner Limit in the mode|125|Maximum|  
|Max Receive RU Size in the mode|00521|SENDSize|  
|Max Send RU Size in the mode|00521|RECEIVESize|  
|LU Name for remote APPC LU|CICSLU|APPLID|  

 The parameter called Maximum has two values, 250 and 125, separated by commas. The first value (250) is the parallel session limit. The second value (125) is the host minimum contention winner limit. On Host Integration Server, this corresponds to Partner Min Contention Winner Limit in the mode. In addition, because the host is the contention winner on 125 sessions (out of a total of 250), Host Integration Server should be configured as the contention winner on the remaining 125 sessions. In this case, Host Integration Server mode would have the following values:  

-   Parallel Session Limit 250  

-   Minimum Contention Winner Limit 125  

-   Partner Min Contention Winner Limit 125  

-   Automatic Activation Limit 0  

## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)