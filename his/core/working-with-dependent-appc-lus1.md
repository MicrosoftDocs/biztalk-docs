---
description: "Learn more about: Working with Dependent APPC LUs"
title: "Working with Dependent APPC LUs1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Working with Dependent APPC LUs
To communicate with a remote TP, a dependent local APPC LU requires the support of a mainframe. You can't use dependent APPC LUs to communicate with IBM i computers. Unlike independent APPC LUs, dependent APPC LUs only allow a single session per LU.  
  
 Dependent APPC LUs are helpful when configuring Host Integration Server to communicate with a mainframe using a version of VTAM earlier than V3R2. Independent LUs are not supported in earlier VTAM versions. Support for dependent APPC LUs is provided with Host Integration Server for compatibility with older VTAM versions. If possible, use independent LUs.  
  
 When configuring APPC dependent LUs, you should specify the network name and LU name. Even though they are not required, they are used by software running on the Host Integration Server computer, such as the Windows Event Log. For example, if a remote APPC LU will be partnered with a dependent local APPC LU, naming the remote APPC LU helps to identify any events associated with the LU in the Windows Event Log.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)
