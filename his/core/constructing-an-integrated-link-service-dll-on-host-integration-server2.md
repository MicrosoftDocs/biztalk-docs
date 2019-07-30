---
title: "Constructing an Integrated Link Service DLL on Host Integration Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ed41551-190b-4446-8645-4d7ba8463d5a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Constructing an Integrated Link Service DLL on Host Integration Server
Microsoft Host Integration Server provides an enhanced method for installing integrated link services that enables remote setup and administration of new link services, as well as support for setup and configuration using a command-line tool. This feature is based on the link service provider supplying a setup and configuration DLL exporting a specific list of functions. A developer must follow certain standards for using this SNA link service configuration DLL (linkcfg) and set various keys and values as registry settings to be used by Host Integration Server for link service configuration.  
  
 To support vendors using these setup and configuration features, Host Integration Server includes the source code for a sample generic Synchronous Data Link Control (SDLC) link service configuration DLL. Also included for use by developers is the source code to a library of utility functions (lnktools) that are commonly useful when implementing the linkcfg DLL. This sample code and the documentation that follows can be used as a guideline for vendors developing similar link service configuration DLLs for their hardware.. Samples include files, C++ files, resource files, makefiles, and project files are included for use with Microsoft Visual C++ version 6.0 and later.  
  
## In This Section  
  
-   [Components of an Integrated Link Service Configuration DLL on Host Integration Server](../core/7896641e-8f96-4317-9dc1-13cb983ee990.md)  
  
-   [Contents of IHVLinks Sample Kit on Host Integration Server](../core/contents-of-ihvlinks-sample-kit-on-host-integration-server1.md)