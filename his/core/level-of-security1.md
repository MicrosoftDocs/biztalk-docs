---
title: "Level of Security1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cae64084-fd8a-420a-894d-e3be55f82523
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Level of Security
Application-level (or package-level) security and user-level security are the two preferred means of authentication because they integrate security on the mainframe with Windows security. The Transaction Integrator (TI) run-time environment obtains credentials from either the Windows identity of the COM+ application or from the identity of the client application that invoked the TI Automation server that contains the TI component.  
  
 In both cases, the facilities of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Enterprise Single Sign-On (ESSO) are required. The Windows credentials are `replicated`, `unchanged`, or `mapped` to another set of credentials specific to the mainframe. The credentials are then sent to the mainframe for authentication.  
  
 Internally, the mechanism functions as follows. For COM+ application identity credentials, TI sets the user ID and password fields in the MC_ALLOCATE verb to MS$SAME, and sets the security field to AP_PGM. This informs HSI to derive host credentials for the owner of the currently executing process.  
  
 For user credentials, TI sets the security field in the MC_ALLOCATE verb to AP_PGM OR'd with AP_PROXY, and fills in the domain and account name fields in the verb ctl block with the values it obtained from `LookupAccountSid` (in the Win32 API). This informs ESSO to derive host credentials corresponding to that Windows account, regardless of the running process. In other words, the run process acts as a proxy for the real user and passes the real user's credentials.  
  
## See Also  
 [Security Implications](../core/security-implications1.md)