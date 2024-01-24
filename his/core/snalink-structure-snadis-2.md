---
description: "Learn more about: SNALink Structure (SNADIS)"
title: "SNALink Structure (SNADIS)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNALink Structure (SNADIS)
A Host Integration Server SNALink consists of the following:  
  
- The link-specific protocol code provided by the independent hardware vendor (IHV)  
  
- A Base  
  
- A Dynamic Access Module (DMOD)  
  
  The DMOD, Base, and the IHV link-specific component of a Host Integration Server SNALink are implemented as dynamic-link libraries (DLLs). The executable component SNALINK.EXE is used to start a SNALink. SNALINK.EXE determines (from the Host Integration Server configuration) which link support DLL (for example, IHVLINK.DLL) is required and dynamically loads it before entering the Base scheduler.  
  
  The following figure shows the executable structure of a SNALink.  
  
  ![Image that shows an executable structure of an SNALink.](../core/media/dev1c.gif "dev1c")  
  Executable structure of an SNALink
