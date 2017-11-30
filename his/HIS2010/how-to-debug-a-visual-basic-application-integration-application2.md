---
title: "How to Debug a Visual Basic Application Integration Application2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4818b38-68fe-4cdd-90ec-94ac22023bc3
caps.latest.revision: 3
---
# How to Debug a Visual Basic Application Integration Application
The following tips will help prevent frustrating debugging sessions:  
  
-   When a Transaction Integrator (TI) .NET Framework application is configured to display error numbers (err.number), the number returned is always 0 and not the TI error results. Although TI returns the correct values to COM Interop and COM Interop passes the right values to Visual Basic, Visual Basic considers any positive return code to be success and changes it to 0. To work around this problem, configure the .NET Framework application to return an error description (err.description) instead of the error number. The error description provides accurate and useful error information.  
  
-   TI Project parameter type Integer must be defined as a short within Visual Basic.  
  
-   TI Project parameter type Long must be defined as an integer within Visual Basic.  
  
-   A Visual Basic array index begins at 0, the index of TI parameters defined as arrays starts at position 1. Therefore, it is no longer possible to directly align one for one the index of TI parameters defined as arrays with those defined within Visual Basic.  
  
-   Arrays of Decimal data types must be defined as an array of objects, not an array of decimals within Visual Basic. All other arrays of data types can be defined as either an object or data type.  
  
-   A common cause of errors during development of host-initiated processing (HIP) .NET Framework components is forgetting to copy all the required assemblies, including all the dependencies, to the HIP Implementing Assemblies folder.  
  
## See Also  
 [Programming Windows-Initiated Processing](../HIS2010/programming-windows-initiated-processing2.md)