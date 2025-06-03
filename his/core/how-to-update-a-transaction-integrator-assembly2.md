---
description: "Learn more about: How to Update a Transaction Integrator Assembly"
title: "How to Update a Transaction Integrator Assembly2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
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
