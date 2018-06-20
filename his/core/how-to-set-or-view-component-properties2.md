---
title: "How to Set or View Component Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1ae824e-3d91-4ac9-9c3f-8f5e54787f10
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Set or View Component Properties
A property sheet displays basic information about a Transaction Integrator (TI) component. Property sheets are available in Host Integration Server Designer (HIS Designer) for the following:  
  
-   Interface.  
  
-   Each method in an interface.  
  
-   Each parameter of a method.  
  
-   Each recordset in an interface.  
  
-   Each column of a recordset.  
  
-   Each user-defined type in an interface.  
  
-   Each member of a user-defined type.  
  
### To view or set an item's properties  
  
1. In HIS Designer, right-click the item, and then click **Properties**.  
  
   > [!NOTE]
   >  After you deploy a TI-created component in a COM+ application, that component acquires additional properties. For a complete view of a component's properties, use TI Manager to view the properties for the component and the properties for the COM+ application where the component is located.  
  
   Some properties are informational only, so you cannot change them. However, there are many properties that you can change. When you are viewing properties in HIS Designer, you can protect against inadvertently changing a component definition by locking the definition. Doing so makes property settings read-only until you unlock them.  
  
### To lock or unlock a component definition in HIS Designer  
  
1.  Start HIS Designer, and open a TI component.  
  
2.  In the console tree, right-click the component's interface, and then click **Lock** or **Unlock**.  
  
     Context-sensitive Help is available for all properties.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)