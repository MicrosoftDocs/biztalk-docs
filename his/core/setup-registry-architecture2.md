---
title: "Setup Registry Architecture2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be67adf4-0072-4387-ac29-c63f4b04f2ec
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Setup Registry Architecture
There are two main subtrees in the Microsoft Windows registry where information is kept relevant to Host Integration Server: the **SOFTWARE** tree and the **SYSTEM** tree. Both of these are subtrees of **HKEY_LOCAL_MACHINE**. The **SOFTWARE** tree contains generic information about independent hardware vendor (IHV) link services, and the **SYSTEM** tree contains information about the individual components of those services. While reading the following topics, it may be helpful to view examples of what is being discussed by inspecting the registry of an existing system with several of the built-in link services installed.  
  
## In This Section  
  
-   [Product Entries](../core/product-entries1.md)  
  
-   [Service Entries](../core/service-entries2.md)