---
title: "Configuration Wizard, Runtime Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.config.wizard.runtime"
ms.assetid: a72538d7-aa60-4374-86e5-951a052d0e00
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Wizard, Runtime Page

## Enable runtime and create hosts
Use the **Runtime** page to configure the BizTalk Server runtime on this computer.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable BizTalk Server runtime components on this computer**|Select **Enable BizTalk Server runtime components on this computer** to enable host creation on this computer.|  
|**Create In-Process Host and Instance**|Select **Create In-Process Host and Instance** to create a host application on this computer.<br /><br /> **Trusted**: Select this if you want to pass the credentials (SSID and/or Party ID) of the sender when submitting messages to the MessageBox database. This is equivalent to creating a trust relationship between the servers.<br /><br /> **Host name**: Type the name of the BizTalk Host. By default this is `BizTalkServerApplication`.|  
|**Create Isolated Host and Instance**|Select **Create Isolated Host and Instance** to create an isolated host application on this computer.<br /><br /> **Trusted**: Select this if you want to pass the credentials (SSID and/or Party ID) of the sender when submitting messages to the MessageBox database. This is equivalent to creating a trust relationship between the servers.<br /><br /> **Isolated Host name**: Type the name of the BizTalk Host. By default this is `BizTalkServerIsolatedHost`.|  
|**Windows Service**|The Windows Service list provides an editable view of the account used to run the BizTalk Host and Isolated Host Windows Services.|  
|**Windows Groups**|The Windows Groups list provides an editable view of the BizTalk Host and Isolated Hosts Windows groups.|  
  
## See Also  
Install [BizTalk Server 2016](../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md) or [BizTalk Server 2013 or R2](../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)    
 [Getting Started](../core/getting-started-with-biztalk-server.md)