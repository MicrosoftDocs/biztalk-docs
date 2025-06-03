---
description: "Learn more about: Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking"
title: "Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking
> [!NOTE]
>  This topic is applicable only for Windows Server 2003.

 You should disable the Windows Server 2003 Service Pack 1 and Service Pack 2 denial of service checking. This is because under certain high-load scenarios, Windows Server 2003 SP1 and SP2 denial of service checking may incorrectly identify valid TCP/IP connections as a denial of service attack.

> [!IMPORTANT]
>  You should disable this feature only in an intranet scenario when you are sure you will not suffer from actual denial of service attacks.

## How Denial of Service Can Affect TCP/IP Connections
 Windows Server 2003 SP1 and SP2 implement a security feature that reduces the size of the queue for concurrent TCP/IP connections to the server. This feature helps prevent denial of service attacks. Under heavy load conditions, the TCP/IP protocol in Windows Server 2003 SP1 or later may incorrectly identify valid TCP/IP connections as a denial of service attack. This may occur when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is under heavy load.

## Modifying the Registry Entry

Create the **SynAttackProtect** registry entry on computers running SQL Server that host [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and on any computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that are running Windows Server 2003 SP1 or later.

## Tuning Registry Settings that Govern the Level of Denial of Service Attack Protection

In certain scenarios you may want to maintain denial of service protection but reduce how aggressively the denial of service functionality is applied. It is possible to tune the default behavior of the denial of service protection feature by following these steps:

1. Ensure that the **SynAttackProtect** registry entry is set to a REG_DWORD value of **1** as described at [SynAttackProtect](/previous-versions/windows/it-pro/windows-server-2003/cc781167(v=ws.10)).

2. Configure the **TcpMaxHalfOpen** registry entry as described at [TcpMaxHalfOpen](/previous-versions/windows/it-pro/windows-server-2003/cc779982(v=ws.10)).

3. Configure the **TcpMaxHalfOpenRetried** registry entry as described at [TcpMaxHalfOpenRetried](/previous-versions/windows/it-pro/windows-server-2003/cc779086(v=ws.10)).

## See Also
 [Operational Readiness Checklists](../technical-guides/operational-readiness-checklists.md)
