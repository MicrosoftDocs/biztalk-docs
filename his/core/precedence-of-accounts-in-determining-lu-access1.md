---
title: "Precedence of Accounts in Determining LU Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9446d298-27c9-4042-b7eb-3d3defee9910
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Precedence of Accounts in Determining LU Access
When user and group account memberships overlap, the highest-priority account that contains a 3270 LU or pool determines the access the user gets. Accounts are prioritized as follows:  
  
1. User accounts (highest priority)  
  
2. Subdomain groups  
  
3. Local groups  
  
4. Well-known groups such as Everyone (lowest priority)  
  
   For example, if a 3270 LU called LU 1 is assigned to a user account (a high-priority account) called JOHND, and at the same time an LU called LU 2 is assigned to a local group (a low-priority account) of which JOHND is a member, JOHND will be given access to LU 1, not LU 2.  
  
## See Also  
 [LUA Access](../core/lua-access2.md)   
 [Downstream Connections (3270)](../core/downstream-connections-3270-2.md)   
 [Host Integration Server 3270 Connectivity](../core/host-integration-server-3270-connectivity2.md)