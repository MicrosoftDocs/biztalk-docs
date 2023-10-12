---
description: "Learn more about: Host Instance Service Properties in Services"
title: "Host Instance Service Properties in Services"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Host Instance Service Properties in Services
## Host Instance Service Properties in Services

When a BizTalk host instance is created, a service in Services is also created. The following information discusses the most common properties:

- General: **Startup Type**

  Default is set to **Automatic** to allow the host instance to automatically start when the computer is restarted. In a Production environment, this property is normally always set to **Automatic**.

- Log On: **Account**

  Set to the user account specified when BizTalk is configured or when a new host instance is created. When BizTalk and SQL Server are on different computers, the account must be a domain account. If BizTalk and SQL Server are on the same computer, the account can be a domain account or a local account.

- Recovery: **First failure**

  Default is set to **Restart the Service**. If the host instance stops unexpectedly the first time, then this setting will attempt to restart the host instance.

  - If the host instance starts successfully and then immediately stops, then the **Second failure** property is applied.
  - If the host instance fails to start, then the **Second failure** property will not apply. No additional restart attempts will be made. The host instance will remain stopped.

- Recovery: **Second failure**

  Default is set to **Restart the Service**. If the host instance stops unexpectedly the second time, then this setting will attempt to restart the host instance.

  - If the host instance starts successfully and then immediately stops, then the **Subsequent failures** property is applied.
  - If the host instance fails to start, then the **Subsequent failure** property will not apply. No additional restart attempts will be made. The host instance will remain stopped.

- Recovery: **Subsequent failures**

  Default is set to **Restart the Service**. If the host instance stops unexpectedly the third time, then this setting will attempt to restart the host instance.

  - If the host instance starts successfully and then immediately stops, then the **Subsequent failures** property will continue to be applied.
  - If the host instance fails to start, then the **Subsequent failure** property will not apply. No additional restart attempts will be made. The host instance will remain stopped.

- Recovery: **Restart service after**

  Default is 1 minute and can be increased if needed.

- Dependencies

  **All** the listed components must be started before the BizTalk host instance will start. This includes Enterprise Single Sign-On.

>[!NOTE]
> The BizTalk host instances properties in Services are also stored in the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTSSvc$*BizTalkHostName* registry key.

### Recovery
 The Recovery capability in Services does not provide indefinite service restart attempts when the host instance service fails to start. By modifying the Recovery properties, it is possible to improve uptime of a BizTalk host instance. The most common scenarios that would cause a BizTalk host instance to stop include:

- Loss of network connectivity with the SQL Server

- Out Of Memory exception

- Access Violation

  **Potential Scenarios**

- The SQL Server goes down unexpectedly. In this situation, the **First Failure** property will apply. With the default **First Failure** and **Restart service after** settings, a single restart attempt is made after 1 minute. If the SQL Server is still not available after 1 minute, no additional restart attempts will be made. The host instance will remain stopped.

- SQL Server is clustered and a failover occurs. The failover takes more than 5 minutes. In this scenario, the default **First Failure** and **Restart service after** settings will attempt a single restart after 1 minute. The restart will fail because SQL Server is still offline. As a result, no additional restart attempts will be made. The host instance will remain stopped.

  **Recommendations**

- When stopping the SQL Server or failing over a SQL cluster, manually stop the BizTalk host instances. After the SQL Server is online, restart the host instances.

- If it is a common occurrence for a SQL cluster failover to take longer than 1 minute, increase the **Restart service after** value to however long it takes the SQL cluster to be online.

- When SQL Server is maintained by a non-BizTalk Administrator, consider increasing the **Restart service after** value. Non-BizTalk Administrators tend to stop/start SQL Server without realizing the impact on BizTalk.

## See Also
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)
