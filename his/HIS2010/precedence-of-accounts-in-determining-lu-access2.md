---
title: "Precedence of Accounts in Determining LU Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b8c3601-d65d-4e58-8b02-18726aa41c7c
caps.latest.revision: 4
---
# Precedence of Accounts in Determining LU Access
When user and group account memberships overlap, the highest-priority account that contains a 3270 LU or pool determines the access the user gets. Accounts are prioritized as follows:  
  
1.  User accounts (highest priority)  
  
2.  Subdomain groups  
  
3.  Local groups  
  
4.  Well-known groups such as Everyone (lowest priority)  
  
 For example, if a 3270 LU called LU 1 is assigned to a user account (a high-priority account) called JOHND, and at the same time an LU called LU 2 is assigned to a local group (a low-priority account) of which JOHND is a member, JOHND will be given access to LU 1, not LU 2.  
  
## See Also  
 [LUA Access](../HIS2010/lua-access1.md)   
 [Downstream Connections (3270)](../HIS2010/downstream-connections-3270-1.md)   
 [Host Integration Server 3270 Connectivity](../HIS2010/host-integration-server-3270-connectivity1.md)