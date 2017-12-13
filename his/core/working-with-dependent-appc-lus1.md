---
title: "Working with Dependent APPC LUs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdd3d653-8823-4428-bb1c-aad8fda608a4
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with Dependent APPC LUs
A dependent local APPC LU requires the support of a mainframe in order to communicate with a remote TP. Dependent APPC LUs cannot be used to communicate with AS/400s. Unlike independent APPC LUs, dependent APPC LUs only allow a single session per LU.  
  
 Dependent APPC LUs are helpful when configuring Host Integration Server to communicate with a mainframe using a version of VTAM earlier than V3R2. Independent LUs are not supported in earlier VTAM versions. Support for dependent APPC LUs is provided with Host Integration Server for compatibility with older VTAM versions. If possible, use independent LUs.  
  
 When configuring APPC dependent LUs, you should specify the network name and LU name. Even though they are not required, they are used by software running on the Host Integration Server computer, such as the Windows Event Log. For example, if a remote APPC LU will be partnered with a dependent local APPC LU, naming the remote APPC LU helps to identify any events associated with the LU in the Windows Event Log.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)