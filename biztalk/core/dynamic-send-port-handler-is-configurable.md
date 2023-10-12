---
description: "Learn more about: Dynamic Send Port Handler is Configurable"
title: "Dynamic Send Port Handler is Configurable"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Dynamic Send Port Handler is Configurable
When creating a Dynamic Send Port, an adapter Send Handler is configurable for *every* installed adapter. Consider the following scenario:

 **Scenario**

 There are two ESB itineraries in an application. Itinerary1 uses a Dynamic Send Port to send data to a File share. Itinerary2 uses a Dynamic Send Port to send e-mail. In the past, Dynamic send ports execute in the adapter's default host. Itinerary1 is designed to target a low volume - big message size scenario. Itinerary2 targets a high volume - small message size scenario. Since there is only one default host for an adapter, all messages are routed using the same host, decreasing the performance.

 **The Change**

 To improve the performance of Dynamic Send Ports, an adapter Send Handler is configurable to use any host. In the ESB scenario, Itinerary1 uses HostA to send data to a File share. Itinerary2 uses HostB Port to send e-mail.

## Select a Send Handler
 When creating a Dynamic One-Way Send Port or Dynamic Solicit-Response Send Port, the Send Handler is configurable for every installed adapter. Steps:

1. In the **BizTalk Server Administration** console, expand **BizTalk Group [*GroupName*]**, expand **Applications**, and then expand the application to contain the send port.

2. Right-click **Send Ports**, click **New**, and then click **Dynamic One-way Send Port** or **Dynamic Solicit-Response Send Port**.

3. In  **Properties**, click **Configure**.

    The adapters are listed with the default Send Handler. Click the down arrow to select a different host.

4. Click **OK** save the settings.

5. Unenlist and reenlist the new dynamic send port.

6. Restart the original host instance.

7. Restart the new host instance.

   Additional Send Port configuration options include:

- [How to Configure Transport Advanced Options for a Send Port](how-to-configure-transport-advanced-options-for-a-send-port.md)

- [How to Configure Backup Transport Options for a Send Port](how-to-configure-backup-transport-options-for-a-send-port.md)

- [How to Configure Outbound Maps for a Send Port](how-to-configure-outbound-maps-for-a-send-port.md)

- [How to Configure Filters for a Send Port](how-to-configure-filters-for-a-send-port.md)

- [How to Assign a Certificate to a Send Port](how-to-assign-a-certificate-to-a-send-port.md)

- [How to Configure Tracking for a Send Port](how-to-configure-tracking-for-a-send-port.md)

  The different hosts can be fine-tuned. The following links discuss performance optimization:

  [General BizTalk Server Optimizations](../technical-guides/general-biztalk-server-optimizations1.md)

  [Managing BizTalk Server Performance Settings](managing-biztalk-server-performance-settings.md)
