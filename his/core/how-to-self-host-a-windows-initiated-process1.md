---
title: "How to Self-Host a Windows-Initiated Process1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be155fc3-9e49-4bc2-bf88-5e2e35cfa38a
caps.latest.revision: 3
---
# How to Self-Host a Windows-Initiated Process
Self-Hosting is a technology that allows you the option of running a Transaction Integrator (TI) assembly in-process with an associated application. Self-Hosting improves performance of your application by not running the TI assembly through Internet Information Services (IIS).  
  
### To self-host a TI assembly  
  
1.  Create a TI assembly as you would normally.  
  
     For more information, see [Creating an Application with Host Integration Server Designer](../core/creating-an-application-with-host-integration-server-designer2.md).  
  
2.  Register the TI assembly using TI Manager, using the **Self-Host** radio button selected.  
  
     You may also set the hosting model in the Properties toolbox in Visual Studio.  
  
     For more information, see [Creating an Object](../core/creating-an-object1.md).  
  
3.  In Visual Studio, use Solution Explorer to add a reference to your TI assembly.  
  
4.  Code your application, using the interfaces on the TI assembly as you would any other interface.  
  
## See Also  
 [Programming Windows-Initiated Processing](../core/programming-windows-initiated-processing2.md)