---
title: "Support for LUA Single Sign-On1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6449c984-5f07-4958-9707-782d5340eb4c
caps.latest.revision: 4
---
# Support for LUA Single Sign-On
This section describes the logical unit application (LUA) support for Single Sign-On using 3270 display sessions that is available in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)].  
  
 Over 3270 LUs, a Single Sign-On feature for LUA applications is supported to automate the overall logon process. When configured for this feature, [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] automatically replaces special keywords in the data stream with the actual host user name and password at appropriate points in the session.  
  
> [!NOTE]
>  Single Sign-On is not supported over LUA logical units (LUs).  
  
 To open 3270 LUs from an LUA application using Request Unit Interface (RUI), the **lua_resv56[1]** field must be set to a nonzero value when this verb control block (VCB) is passed to [RUI_INIT](../Topic/RUI_INIT2.md). To open 3270 LUs from an LUA application using a Session Level Interface (SLI), the **lua_resv56[2]** field must be set to a nonzero value when this VCB is passed to [SLI_OPEN](../core/sli-open.md). For details, see the reference sections in [RUI_INIT](../Topic/RUI_INIT2.md) and [SLI_OPEN](../core/sli-open.md).  
  
 This section contains:  
  
-   [Prerequisites for LUA Single Sign-On](../core/prerequisites-for-lua-single-sign-on.md)  
  
-   [Registry Settings Used for LUA Single Sign-On](../core/registry-settings-used-for-lua-single-sign-on.md)  
  
-   [LUA User Name and Password Replacement](../core/lua-user-name-and-password-replacement.md)