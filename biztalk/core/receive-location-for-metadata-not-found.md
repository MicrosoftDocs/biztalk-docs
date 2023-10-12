---
description: "Learn more about: Receive location for metadata not found"
title: "Receive location for metadata not found"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Receive location for metadata not found
## Details  
  
| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                           |
| Product Version |                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                       |
|    Event ID     |                                                                   0                                                                   |
|  Event Source   |                                                                   0                                                                   |
|    Component    |                                                                   0                                                                   |
|  Symbolic Name  |                                                                   0                                                                   |
|  Message Text   | Receive location "{0}" for metadata not found. (Check receive location mapping in Web.config and verify the receive location exists.) |
  
## Explanation  
 This error indicates that a published isolated WCF receive location could not find the corresponding receive location for metadata.  
  
## User Action  
 To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.  
  
 For additional information on receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Publishing WCF Services](../core/publishing-wcf-services.md)  
  
-   [How to Configure a WCF-BasicHttp Receive Location](wcf-basichttp-adapter.md)  
  
-   [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)
