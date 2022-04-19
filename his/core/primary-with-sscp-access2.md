---
description: "Learn more about: Primary with SSCP Access"
title: "Primary with SSCP Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cdce08e-1e9c-4133-b995-986cecd33b8e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Primary with SSCP Access
To initialize a session by having the Session Level Interface (SLI) wait for a BIND and SDT but allow system services control point (SSCP) access, set **open.lua_init_type** to LUA_INIT_TYPE_PRIM_SSCP. Rather than sending commands to the host to begin a session, the SLI enables the Windows logical unit application (LUA) application to issue [SLI_SEND](../core/sli-send2.md) and [SLI_RECEIVE](../core/sli-receive2.md) for the SSCP normal flow only. This allows the INITSELF commands or LOGON messages and responses to be transmitted between the Windows LUA application and the host. The application can have more than one INITSELF and LOGON message. For this type of session only, other SLI verbs can be issued before [SLI_OPEN](../core/sli-open2.md) completes. When issuing **SLI_SEND**, an application should not specify any flow flag unless the application is sending a response, as specified in the **lua_message_type** parameter of **SLI_OPEN**. To obtain the INIT_COMPLETE status, the application must first issue **SLI_OPEN**, and then issue either [SLI_BID](../core/sli-bid2.md) or **SLI_RECEIVE**. The INIT_COMPLETE status notifies the application that the **SLI_SEND** and **SLI_RECEIVE** verbs for SSCP normal flow data can be issued.
