---
description: "Learn more about: Configuring LUs"
title: "Configuring LUs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b94f422-512a-4e0a-a64f-22def10fc043
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring LUs
When a user configures a 5250 emulator to access an AS/400, the emulator is configured with the local and remote APPC LU alias names. The LU alias names are mapped to LU names that are used for the conversation with the IBM System i.  
  
 Host Integration Server allows you to define a default local and remote APPC LU for each user group accessing the IBM System i. Setting default values relieves the user from having to remember APPC LU names; these values should be specified, if possible.  
  
 When creating local APPC LUs, it is recommended that you use the name of a user or group as the local LU alias. When the session from a particular user or group is active, the LU alias name is displayed in SNA Manager. Matching local LU alias names with user names allows you to tell which 5250 users are connected to the IBM System i. This also makes it easy to keep track of which local LU a particular user should use.  
  
 To use this method, create a separate local APPC LU with an LU alias that matches the user name of each person or group being added to the SNA subdomain. After the LU is created, assign the LU to the user as the default local APPC LU along with a default remote APPC LU.  
  
 In Host Integration Server, you can also specify an implicit incoming remote LUthat defines the properties to use when Host Integration Server receives a request to start a session with a local LU, and the remote LU named in the request is not recognized by Host Integration Server. You can also specify an implicit incoming mode that defines the session characteristics when a mode is not recognized by Host Integration Server.  
  
 If you want to accept an incoming request that can arrive by many different remote LUs without explicitly defining each remote LU, you can specify implicit incoming remote LU pairs, along with their mode. When the implicit incoming remote LU and mode are specified, the remote LU does not need to be recognized by the server. As long as the local LU specified in the session request is recognized, the connection can be initiated.  
  
## See Also  
 [APPC Deployment Strategies](../core/appc-deployment-strategies1.md)
