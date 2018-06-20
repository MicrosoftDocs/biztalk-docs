---
title: "Receive location for address not found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 637f3925-06ff-47b2-99db-f85e829ee318
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive location for address not found
## Details  
  
|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  Product Name   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| Product Version |                  [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                   |
|    Event ID     |                                               0                                               |
|  Event Source   |                                               0                                               |
|    Component    |                                               0                                               |
|  Symbolic Name  |                                               0                                               |
|  Message Text   | Receive location for address "{0}" not found. (The BizTalk receive location may be disabled.) |
  
## Explanation  
 This error indicates that a published isolated WCF receive location could not find the corresponding receive location.  
  
## User Action  
 To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.  
  
 For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [How to Configure a WCF-BasicHttp Receive Location](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)