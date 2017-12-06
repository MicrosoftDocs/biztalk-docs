---
title: "How to Assign a TI Component to a Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 025b6170-0028-44c4-a23c-bc22856ed124
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Assign a TI Component to a Remote Environment
Each TI component is associated with a remote environment (RE) type. As you add multiple REs of the same type, verify that each component is assigned to an RE of the type for which it is configured.  
  
 To assign a component to a specific RE of the appropriate type, you can use one of the following methods:  
  
-   Set a default RE for the Transaction Integrator (TI) components you create. When you deploy the TI component in a COM+ application , the component is automatically associated with the default RE of the appropriate type. Unless you specifically set the default RE, the default RE is the first RE of that type (or class) that you defined.  
  
-   Manually move components from one specific instance of an RE type to another specific instance of the same type. This action applies to TI components that you have already deployed in a COM+ application. You can use TI Manager to move components from one RE to another.  
  
-   Deploy the TI component by using HIS Designer. In HIS Designer, you are asked to associate the TI component with a specific RE. For more information about this option, see [How to Deploy a TI Component &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/76d17904-c65d-4427-94ad-7f57e9268cd6).  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager.md)   
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components.md)   
 [Getting Started with TI](../core/getting-started-with-ti.md)