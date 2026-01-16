---
title: Connections for IBM i
description: Learn more about connections for IBM i.
ms.service: host-integration-server
ms.topic: concept-article
ms.date: 11/28/2023
---

# IBM i connections

When you use exchange identification (XID) with IBM i computers, the Network Name and Control Point Name are used together as the identifiers and are called the fully qualified name. Make sure that the following items match. If they don't, Host [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] doesn't identify itself in a way that the IBM i can recognize.
  
| Identifier used on IBM i | Identifier to configure <br><br> on Host Integration Server |
|---------------------------------|-------------------------------------------------------------|
| **RMTNETID** (usually and often set to APPN); **RMTCPNAME** | **Local Network Name** and **Local Control Point Name** (configured on the server) |
| **RMTNETID** (often set to APPN); **CP Name** (shown in the **Display network attributes** screen) | **Remote Network Name** and **Remote Control Point Name** (configured on the connection) |

Event log entries can be very helpful in diagnosing and correcting mismatched identifiers between Host Integration Server and host computers.

## See also

[Host Configuration](../core/host-configuration1.md)
