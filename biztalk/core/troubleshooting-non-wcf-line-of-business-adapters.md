---
title: "Troubleshooting non-WCF Line of Business Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d5f7877-656f-406e-9edb-d6b9a0705b02
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting non-WCF Line of Business Adapters
## “Failed to retrieve” error  
 When using a non-WCF Line of Business (LOB) adapter, the following errors may occur:  
  
-   Failed to retrieve system  
  
-   Browsing agent: Error trapped in constructor. Target machine Actively refused connection.  
  
-   Runtime agent: Error trapped in constructor. Target machine Actively refused connection.  
  
### Cause  
 The LOB adapters use .Net Remoting. If the .Net Remoting activation takes longer than expected, the adapter may return these errors.  
  
### Resolution  
 Create the **StartAgentSleep** registry key and increase the timeout value:  
  
1. Open the registry and go to *HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*.  
  
2. Create a new DWORD value with the following properties:  
  
    Name: StartAgentSleep  
  
    Base: Decimal  
  
    Value data: 1000  
  
   Value data is measured in milliseconds (ms). 1000ms equals 1 second.  
  
   In some systems, one second may not be enough. Increase the value and test to help determine the appropriate timeout needed.  
  
> [!IMPORTANT]
>  Adding the **StartAgentSleep** registry key impacts **all** the non-WCF LOB adapters.  
  
## See Also  
 [Troubleshooting BizTalk Server Adapters](../core/troubleshooting-biztalk-server-adapters.md)