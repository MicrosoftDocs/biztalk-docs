---
title: "Command Request Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65f740dd-8930-49b9-9add-0e0efa8c440b
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Command Request Support
The next three tables list the SNA command requests supported by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Note that not all commands are supported for every LU-to-LU session type. For example, Bracket Initiation Stopped (BIS) is only supported for use by an APPC LU.  
  
 The following three tables categorize requests in the following order:  
  
1. Session control requests  
  
2. Function management data requests: network services (maintenance) and network services (session)  
  
3. Data flow control requests  
  
   The three tables denote the category for each request by the setting of the request/response unit (RU) category bits in the request/response header (RH), and by the function of the request. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] does not support commands that fall in the network control request category.  
  
   For more information about command requests, see your IBM documentation.  
  
### SNA Request Support for Session Control Requests  
  
|Session|Request|Direction|  
|-------------|-------------|---------------|  
|SSCP-PU|ACTPU|SSCP to PU|  
||DACTPU|SSCP to PU|  
|SSCP-LU|ACTLU|SSCP to SLU|  
||DACTLU|SLU to SSCP|  
|PLU-SLU|BIND|PLU to SLU|  
||UNBIND|PLU to/from SLU|  
||CLEAR|PLU to SLU|  
||SDT|PLU to SLU|  
  
### SNA Request Support for Function Management Data Requests  
  
|Session|Request|Direction|  
|-------------|-------------|---------------|  
|SSCP-PU|NMVT (1)|SSCP to/from PU|  
||INIT-SELF (2)|SLU to SSCP|  
||TERM-SELF (2)|SLU to SSCP|  
||NOTIFY (2)|SLU to SSCP|  
||NSPE (2)|SSCP to SLU|  
  
 1. Network services, maintenance services  
  
 2. Network services, session services  
  
### SNA Request Support for Data Flow Control Requests  
  
|Session|Request|Direction|  
|-------------|-------------|---------------|  
|PLU-SLU|BID|PLU to/from SLU|  
||BIS|PLU to/from SLU|  
||CANCEL|PLU to/from SLU|  
||CHASE|PLU to SLU|  
||LUSTAT|PLU to/from SLU|  
||RTR|PLU to/from SLU|  
||SHUTC|PLU from SLU|  
||SHUTD|PLU to SLU|  
||SIGNAL|PLU to/from SLU|  
  
## See Also  
 [Host Integration Server Support](../core/host-integration-server-support2.md)