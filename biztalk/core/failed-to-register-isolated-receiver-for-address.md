---
description: "Learn more about: Failed to register isolated receiver for address"
title: "Failed to register isolated receiver for address"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Failed to register isolated receiver for address
## Details  
  
| Field | Error Details | 
|-----------------|---------------------------------------------------------------------------------------------------------|
|  Product Name   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]            |
| Product Version |                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                        |
|    Event ID     |                                                    0                                                    |
|  Event Source   |                                                    0                                                    |
|    Component    |                                                    0                                                    |
|  Symbolic Name  |                                                    0                                                    |
|  Message Text   | Failed to register isolated receiver for address "{0}"; receive location does not exist or is disabled. |
  
## Explanation  
 This error indicates that a published isolated WCF receive location could not find the corresponding receive location.  
  
## User Action  
 To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Services Publishing Wizard generated exists and is started.  
  
 For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [How to Configure a WCF-BasicHttp Receive Location](wcf-basichttp-adapter.md)  
  
-   [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)
