---
title: "Specifying a Remote Environment Programmatically2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 683b533f-4273-46fa-9853-e75d50b6ae66
caps.latest.revision: 3
---
# Specifying a Remote Environment Programmatically
When an application uses a Transaction Integrator (TI) component, you can structure the application to explicitly specify the remote environment (RE) used by the TI run-time environment. When the application specifies the RE, the application identifies the CICS or IMS region where transaction programs (TP) are executed when they handle method calls to the component. The specific algorithm an application uses to select an RE is up to you. For example, an enterprise can use separate CICS or IMS regions to handle requests from different branches. In this case, the application should set the RE to the appropriate value that identifies the region suitable for the current branch.  
  
## In This Section  
 This section includes the following topics  
  
-   [How To Use REOverride to Specify a Remote Environment](../HIS2010/how-to-use-reoverride-to-specify-a-remote-environment1.md)  
  
-   [REOverride Guidelines](../HIS2010/reoverride-guidelines2.md)