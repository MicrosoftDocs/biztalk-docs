---
description: "Learn more about: Configuring for LUA"
title: "Configuring for LUA1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d57d1bba-5deb-40b6-9255-937496a5d962
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring for LUA
The Host Integration Server configuration file, which is set up and maintained by the system administrator, contains information that is required for logical unit application (LUA) applications to communicate. An LUA LU is configured by the link service to use a connection to the host, and is given an LU number that matches that of an LU on the host.  
  
 The configuration can include LUA LU pools. A pool is a group of LUs with similar characteristics, and it enables an application to use any free LU from the pool. This feature can be used to allocate LUs on a first-come, first-served basis when there are more applications than LUs available, or to provide a choice of LUs on different connections.  
  
 The following communications components are configured for use with an LUA application.  
  
|Component|Description|  
|---------------|-----------------|  
|Link service|A link service for communicating with the host. This component is normally configured by the Setup program during Host Integration Server installation.|  
|Connection|A connection to the host that uses the link service.|  
|Local node|A local node that owns the connection. This component is configured automatically.|  
|LUA LU|An LUA LU on the local node, configured to use the connection, with an LU number that matches an LU on the host.|  
|LUA LU pool (optional)|If necessary, you can configure more than one LUA LU for the application, and group the LUs into a pool. This means that an application can specify the pool rather than a specific LU when issuing the [RUI_INIT](./rui-init1.md) verb to start a session. Host Integration Server uses this name in one of the following ways:<br /><br /> -   If the name supplied is the name of an LU that is not in a pool, a session is assigned using that LU if it is available (that is, if it is not already in use by an LUA application).<br />-   If the name supplied is the name of an LU pool, or the name of any LU within the pool, a session is assigned using the first available LU in the pool (if one is available). Note that this may not be the LU whose name was specified by the RUI_INIT verb.|
