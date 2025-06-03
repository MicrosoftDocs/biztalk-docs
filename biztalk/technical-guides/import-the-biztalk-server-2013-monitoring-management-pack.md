---
description: "Learn more about: Import the BizTalk Server 2013 Monitoring Management Pack"
title: "Import the BizTalk Server 2013 Monitoring Management Pack"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Import the BizTalk Server 2013 Monitoring Management Pack
For instructions about how to import a management pack, see How to Import a Management Pack in [Operations Manager 2007 R2/2012](/previous-versions/system-center/operations-manager-2007-r2/cc974494(v=technet.10)) (<https://go.microsoft.com/fwlink/?LinkId=142351>). After the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack is imported, follow these procedures to finish your initial configuration:

### To configure the management pack

1.  Create a new management pack in which you store overrides and other customizations.

2.  To enable the Agent Proxy setting, follow these steps:

    1.  Open the Operations console and then click the Administration button.

    2.  In the Administrator pane, click **Agent Managed**.

    3.  Double-click an agent in the list.

    4.  On the Security tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**.

    5.  Repeat steps 3 through 4 for each agent that is installed on a BizTalk Server.
