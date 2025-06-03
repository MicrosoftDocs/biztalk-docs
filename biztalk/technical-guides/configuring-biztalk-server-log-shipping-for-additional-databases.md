---
title: "Configure BizTalk Log Shipping for Additional Databases"
description: Add custom databases to Backup BizTalk Server job, and to Log Shipping in BizTalk Server
ms.custom: ""
ms.date: "11/01/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Configuring BizTalk Server Log Shipping for Additional Databases

## Overview
In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping. You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job. However, be sure to add custom databases as appropriate under the \<OtherDatabases\> section of the SampleUpdateInfo.xml file. [Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) and [Back Up Custom Databases](../core/how-to-back-up-custom-databases.md) provides some guidance.
  
## See Also  
 [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md)
