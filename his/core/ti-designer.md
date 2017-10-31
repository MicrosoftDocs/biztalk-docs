---
title: "TI Designer2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2af1434f-1eb3-46b1-96d7-f7e4c0c07d93
caps.latest.revision: 3
---
# TI Designer
TI Designer is a design-time development tool that is hosted inside, and uses the graphical user interface, of Microsoft Visual Studio. You use TI Designer to set the rules for mapping and resolving data types between a Windows resource (such as .NET Framework or BizTalk Server) and an IBM batch or online transaction program.  
  
 TI Designer creates TI objects stored as .NET Framework assemblies (.dll) describing the methods and data for a mainframe TP. Each TI object includes TI run-time environment settings that associate the object with a specific type of remote environment (RE) class, for example CICS LU 6.2 Link, for the mainframe or midrange host computer. In addition to the description of the methods and Automation parameters, the TI component type library contains custom data describing how data types are mapped between a method in TI Automation server and a mainframe transaction in a COBOL transaction program (TP) or a OS/400  transaction in a RPG transaction program. It also establishes other parameters that affect data conversion at runtime.  
  
 You can also use TI Designer to import or export the data definition section of the COBOL or RPG code making up mainframe transaction programs (TPs). TI Designer can automatically generate a TI object (.dll) from imported COBOL code, or it can export generated COBOL code that you can use in your mainframe TP.  
  
## See Also  
 [Transaction Integrator Components](../core/transaction-integrator-components.md)