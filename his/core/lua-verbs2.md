---
description: "Learn more about: LUA Verbs"
title: "LUA Verbs2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# LUA Verbs
This implementation of logical unit application (LUA) is available to applications written in Microsoft® C++® version 6.0 or later. Applications access all LUA functions on Windows Server by issuing verbs using the external C functions [RUI](./rui2.md),[SLI](./sli2.md),[WinRUI](./winrui1.md), and [WinSLI](./winsli1.md).  
  
 Symbolic constants are defined in the WINLUA.H header file for many parameter values. Refer to the WINLUA.H file (contained in the Microsoft Host Integration Server SDK) for a list of LUA constants.  
  
 You should use the symbolic constant and not the hexadecimal value when setting values for supplied parameters, or when testing values of returned parameters.  
  
 Parameters marked as reserved should always be set to zero.  
  
 This section contains:  
  
-   [RUI and SLI Definitions](../core/rui-and-sli-definitions1.md)  
  
-   [Issuing an LUA Verb](../core/issuing-an-lua-verb2.md)
