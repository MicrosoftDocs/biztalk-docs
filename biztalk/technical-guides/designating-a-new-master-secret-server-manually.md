---
description: "Learn more about: Designating a New Master Secret Server Manually"
title: "Designating a New Master Secret Server Manually"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Designating a New Master Secret Server Manually
Cluster hardware can be expensive. If hardware cost is a concern, you can consider manually designating another Enterprise Single Sign-On (SSO) server to be the master secret server during failure scenarios. Using this option, any other SSO server in the SSO group can be promoted to the master secret server. When the master is down, you can manually promote one of the SSO servers to be the master secret server. The biggest disadvantage of this technique is that you cannot edit the existing deployments, restart the existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services, or deploy new BizTalk applications until you promote a new master secret server.

 To make the process seamless, you will need to implement some monitoring mechanism so you will discover the failure as soon as possible. You can also automate the promotion process by using a monitoring application such as System Center Operations Manager.

 For more information about manually moving the master secret server, see [How to Move the Master Secret Server](../core/how-to-move-the-master-secret-server.md) (<https://go.microsoft.com/fwlink/?LinkId=156841>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.

## See Also
 [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md)