---
description: "Learn more about: Specifying SNA Attributes for Remote Environments"
title: "Specifying SNA Attributes for Remote Environments1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Specifying SNA Attributes for Remote Environments
To determine the attributes that are required by Transaction Integrator (TI) when you are creating a new remote environment, see your [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] configuration. To obtain the required attribute values, open Host Integration Server SNA Manager or contact your [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] system administrator.  
  
> [!NOTE]
>  To use two-phase commit, each local and remote logical unit (LU) must have SyncPoint support enabled in the SNA server node in which it is defined and should point to the computer that is running Resync services. For more information, see [Providing a Fail-Safe Environment for ACID Transactions](./providing-a-fail-safe-environment-for-acid-transactions1.md).  
  
 **Local LU Alias**  
  
 Enter the LU alias for the local APPC LU defined for the TI remote environment. From Host Integration Server SNA Manager, select the Host Integration Server computer that provides the required host connectivity. Then open the Local APPC LUs folder to obtain a list of configured local APPC LU aliases. Use a name from the list to specify this attribute.  
  
 **Remote LU Alias**  
  
 Enter the LU alias for the remote APPC LU defined for the TI remote environment. From Host Integration Server SNA Manager, select the computer running Host Integration Server that provides the required host connectivity. Then open the Remote APPC LUs folder to obtain a list of configured remote APPC LU aliases. Use a name from the list to specify this attribute.  
  
 **Mode Name**  
  
 Enter the APPC mode used for the connection. From Host Integration Server SNA Manager, open the APPC Modes folder to obtain a list of configured modes. Use a name from the list to specify this attribute.  
  
 To use two-phase commit, the APPC mode must be Sync Level 2 capable.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)
