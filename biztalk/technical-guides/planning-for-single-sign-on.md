---
description: "Learn more about: Planning for Single Sign-On"
title: "Planning for Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d1bc220-4087-4603-ac15-6bb0c62c59d4
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Single Sign-On
Enterprise Single Sign-On (SSO) is a critical component of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run time cannot function without the SSO service because all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter configuration information is encrypted and stored in the SSO database and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accesses this information via the SSO service. This adapter configuration information is not accessible if the SSO service is not running on the BizTalk server or if the SSO service does not have access to the SSO master secret server.

 Your SSO implementation should include the following plans.

## Backing Up the Master Secret
 If the SSO master secret server fails and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the SSO database. You must back up the master secret, or you risk losing data from the SSO database. Therefore it is absolutely critical that the SSO master secret is backed up and stored in a secure location. For information about backing up the SSO master secret, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md) (https://go.microsoft.com/fwlink/?LinkId=151395).

## Configuring SSO for High Availability
 Because SSO is such a critical component of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, the SSO master secret server should be configured for high availability. If at all possible, the Enterprise Single Sign-On service on the master secret server should be clustered by following the steps in [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md). In the event that you do not have access to a Windows Server cluster, you can still provide high availability for the Enterprise Single Sign-On service on the master secret server by following the steps documented in the topic [Designating a New Master Secret Server Manually](../technical-guides/designating-a-new-master-secret-server-manually.md).

## Following Established SSO Security Recommendations
 Follow SSO security recommendations described in the topic [SSO Security Recommendations](../core/sso-security-recommendations.md) (https://go.microsoft.com/fwlink/?LinkId=155753).