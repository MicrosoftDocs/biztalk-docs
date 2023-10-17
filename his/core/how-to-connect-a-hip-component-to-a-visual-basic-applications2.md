---
description: "Learn more about: How To Connect a HIP Component to a Visual Basic Applications"
title: "How To Connect a HIP Component to a Visual Basic Applications2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e9e8a91-d48e-418f-a032-475c91212183
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How To Connect a HIP Component to a Visual Basic Applications
A key link in host-initiated processing (HIP) is the connection between the HIP component in Transaction Integrator (TI) and the client application. The connection between the HIP component and the Microsoft Visual Basic server DLL is created through matching elements of the HIP type library with elements of the Visual Basic project. The following table shows the relationship between the elements.  
  
|HIP Type Library|Visual Basic Project|  
|----------------------|--------------------------|  
|Type Library name|Visual Basic Project name.|  
|Type Library Interface name|Visual Basic Class name.|  
|Type Library Method names|Functions or subroutines within the Visual Basic Class.|  
|Type Library method parameters|Defined one for one within the Visual Basic functions or subroutines with the Visual Basic subroutines and functions.|  
  
> [!NOTE]
>  Make sure that the Visual Basic server DLL is registered.  
  
 If you are using the **Implements** key word within a Visual Basic server, the following additional rules apply:  
  
-   The **Visual Basic Implement Compatible Interface** property must be enabled. Set the property on the component *interface* **Properties** page within the TI type library or assembly  
  
-   All parameters defined to type library methods must be **Input\Output**. The **Implements** keyword does not support parameters defined as either input or output. All parameters must be defined as input or output.  
  
-   The function or subroutine calls must be defined as public, not private, within the Visual Basic class.  
  
## See Also  
 [Programming Host-Initiated Processing](../core/programming-host-initiated-processing1.md)
