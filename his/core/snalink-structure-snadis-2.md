---
title: "SNALink Structure (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2b45021-9d76-4e25-bb1b-3e8432d27a77
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNALink Structure (SNADIS)
A Host Integration Server SNALink consists of the following:  
  
- The link-specific protocol code provided by the independent hardware vendor (IHV)  
  
- A Base  
  
- A Dynamic Access Module (DMOD)  
  
  The DMOD, Base, and the IHV link-specific component of a Host Integration Server SNALink are implemented as dynamic-link libraries (DLLs). The executable component SNALINK.EXE is used to start a SNALink. SNALINK.EXE determines (from the Host Integration Server configuration) which link support DLL (for example, IHVLINK.DLL) is required and dynamically loads it before entering the Base scheduler.  
  
  The following figure shows the executable structure of a SNALink.  
  
  ![](../core/media/dev1c.gif "dev1c")  
  Executable structure of an SNALink