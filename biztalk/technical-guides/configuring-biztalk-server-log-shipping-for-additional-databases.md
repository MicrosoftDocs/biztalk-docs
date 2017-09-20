---
title: "Configuring BizTalk Server Log Shipping for Additional Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc2ae67-5cb9-4d53-9bf7-c88f84914960
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring BizTalk Server Log Shipping for Additional Databases
In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping. You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job. However, be sure to add custom databases as appropriate under the \<OtherDatabases> section of the SampleUpdateInfo.xml file as described in step 22 of [How to Configure the Destination System for Log Shipping](http://go.microsoft.com/fwlink/?LinkId=151402) (http://go.microsoft.com/fwlink/?LinkId=151402) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
## See Also  
 [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md)