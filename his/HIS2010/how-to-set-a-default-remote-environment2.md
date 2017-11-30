---
title: "How to Set a Default Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c808b63c-1d8f-485b-85a6-0dca9e47b181
caps.latest.revision: 3
---
# How to Set a Default Remote Environment
Each Transaction Integrator (TI) component must be associated with a remote environment (RE) type. When you register a TI component by adding it to a COM+ application , the component is associated with the first instance of the same type that you defined using TI Manager. For example, if you create an instance of a CICS using LU 6.2 RE with the default name of CICS1, any component created for use with a CICS using LU 6.2 RE will be associated with CICS1. If you define more REs of the same type (for example, CICS2 and CICS3), you can specify the default RE for associated components that you later deploy.  
  
 If you want to associate a component with an RE at a later time, you can specify a default RE of none. Registered components with no RE specified are shown in the **Unassigned Components** folder in TI Manager.  
  
### To set a default RE  
  
1.  Start TI Manager.  
  
2.  Right-click **Transaction Integrator** in the console tree, and then click Properties.  
  
3.  Click the **Registrar** tab.  
  
4.  Click an RE type, and then click **Change**.  
  
5.  In the list, click the name of the RE that you want to be the default RE instance for that RE type.  
  
6.  Click **OK**.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../HIS2010/creating-and-managing-remote-environments-with-ti-manager2.md)   
 [Creating and Managing TI Components](../HIS2010/creating-and-managing-ti-components1.md)   
 [Getting Started with TI](../HIS2010/getting-started-with-ti2.md)