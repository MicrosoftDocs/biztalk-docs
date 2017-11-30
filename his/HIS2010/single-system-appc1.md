---
title: "Single-System APPC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b86a2141-2689-4508-aac6-70a859d17c0f
caps.latest.revision: 3
---
# Single-System APPC
Single-system APPC has two local APPC LUs residing on the same server. The LUs communicate with each other using defined parameters. You do not need to define a connection because the LUs are communicating with each other on the same system.  
  
 For a single-system APPC, you will need to assign two local APPC LUs to a server, not to a connection. Configuration of the local APPC LUs includes specifying the LU Alias, Network Name, and LU Name. Each of these labels identifies an LU to a particular set of software components.  
  
 If Common Programming Interface for Communications (CPI-C) is used, configure one or more CPI-C symbolic destination names. For more information, see [CPI-C Access](../HIS2010/cpi-c-access1.md) in the next section.  
  
 Single-system APPC is generally used for testing transaction programs. The basic steps for configuring single-system APPC are as follows.  
  
### To configure single-system APPC  
  
1.  Assign two local APPC LUs to a server.  
  
2.  Configure the local APPC LUs by specifying the LU Alias, Network Name, and LU Name.  
  
3.  If an appropriate mode has not already been configured, configure it.  
  
> [!NOTE]
>  For single-system APPC, the Automatic Activation Limit specified in the mode is meaningless. Use one of the local LUs for the originator conversation and the other local LU for the destination conversation.  
  
## See Also  
 [APPC Mode Definition](../HIS2010/appc-mode-definition1.md)   
 [Implicit Incoming Remote LU and Implicit Incoming Mode](../HIS2010/implicit-incoming-remote-lu-and-implicit-incoming-mode2.md)   
 [Default Local APPC LU and the Default Remote APPC LU](../HIS2010/default-local-appc-lu-and-the-default-remote-appc-lu2.md)   
 [Default Outgoing Local APPC LU Pool](../HIS2010/default-outgoing-local-appc-lu-pool2.md)