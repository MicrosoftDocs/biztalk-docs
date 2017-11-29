---
title: "Specifying SNA Attributes for Remote Environments1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f57034bb-5b40-4b2c-81a0-fdef348a491b
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Specifying SNA Attributes for Remote Environments
To determine the attributes that are required by Transaction Integrator (TI) when you are creating a new remote environment, see your [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] configuration. To obtain the required attribute values, open Host Integration Server SNA Manager or contact your [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] system administrator.  
  
> [!NOTE]
>  To use two-phase commit, each local and remote logical unit (LU) must have SyncPoint support enabled in the SNA server node in which it is defined and should point to the computer that is running Resync services. For more information, see [Providing a Fail-Safe Environment for ACID Transactions](../Topic/Providing%20a%20Fail-Safe%20Environment%20for%20ACID%20Transactions2.md).  
  
 **Local LU Alias**  
  
 Enter the LU alias for the local APPC LU defined for the TI remote environment. From Host Integration Server SNA Manager, select the Host Integration Server computer that provides the required host connectivity. Then open the Local APPC LUs folder to obtain a list of configured local APPC LU aliases. Use a name from the list to specify this attribute.  
  
 **Remote LU Alias**  
  
 Enter the LU alias for the remote APPC LU defined for the TI remote environment. From Host Integration Server SNA Manager, select the computer running Host Integration Server that provides the required host connectivity. Then open the Remote APPC LUs folder to obtain a list of configured remote APPC LU aliases. Use a name from the list to specify this attribute.  
  
 **Mode Name**  
  
 Enter the APPC mode used for the connection. From Host Integration Server SNA Manager, open the APPC Modes folder to obtain a list of configured modes. Use a name from the list to specify this attribute.  
  
 To use two-phase commit, the APPC mode must be Sync Level 2 capable.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager.md)