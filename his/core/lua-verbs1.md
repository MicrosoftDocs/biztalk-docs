---
title: "LUA Verbs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4fbc64b5-44fe-4103-9f78-1b1f691ee17a
caps.latest.revision: 4
---
# LUA Verbs
This implementation of logical unit application (LUA) is available to applications written in Microsoft® C++® version 6.0 or later. Applications access all LUA functions on Windows Server by issuing verbs using the external C functions [RUI](../core/rui1.md),[SLI](../core/sli1.md),[WinRUI](../core/winrui2.md), and [WinSLI](../core/winsli2.md).  
  
 Symbolic constants are defined in the WINLUA.H header file for many parameter values. Refer to the WINLUA.H file (contained in the Microsoft Host Integration Server SDK) for a list of LUA constants.  
  
 You should use the symbolic constant and not the hexadecimal value when setting values for supplied parameters, or when testing values of returned parameters.  
  
 Parameters marked as reserved should always be set to zero.  
  
 This section contains:  
  
-   [RUI and SLI Definitions](../core/rui-and-sli-definitions2.md)  
  
-   [Using an LUA Verb](#_sna_using_lua_verbs_lua)