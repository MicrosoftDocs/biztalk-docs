---
title: "How to Update a Transaction Integrator Assembly2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 004c41d8-c0b2-49c5-9768-fda7858c9fe7
caps.latest.revision: 3
---
# How to Update a Transaction Integrator Assembly
If you are upgrading your version of Host Integration Server, you may have Transaction Integrator (TI) assemblies that use a previous version of the .NET Framework. Host Integration Server allows you several options on how to upgrade, so that your assemblies use, so that they may be compatible with the newest version of the .NET Framework.  
  
### To update a TI Assembly  
  
1.  Do nothing.  
  
     If you do not modify your TI assembly in any way, you do not need to upgrade the assembly: .NET Frameworks 2.0 is backwards-compatible with any TI assembly created using .NET Frameworks 1.x.  
  
2.  Open the assembly, make a change, and save the file.  
  
     When you save the file, Host Integration Server will automatically update the TI assembly to the .NET Framework 2.0.  
  
3.  Change the name of the assembly in Visual Studio using the **Save As…** command.  
  
     As with option 2, Host Integration Server will update the assembly when you save the name.