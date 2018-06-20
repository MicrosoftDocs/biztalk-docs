---
title: "Send Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cf61c82-ad48-4555-af53-fb841fd0f503
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Errors
Information for diagnosing and resolving WCF Send errors.  
  
## Failed to generate ODX file

|                 |                                   Error details                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                            Failed to generate ODX file                             |
  
### Explanation  
 This error indicates there was an error in consuming the service.  
  
### User Action  
 Check that the service has valid Web Method and that metadata is hosted (if you own the WCF services). Otherwise, contact the service provider.  
  
 For additional information on consuming WCF services, see [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).
 
## Response message body was not read
  
|                 |                                        Error details                                        |
|-----------------|---------------------------------------------------------------------------------------------|
|  Product Name   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| Product Version |                 [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                  |
|    Event ID     |                                              0                                              |
|  Event Source   |                                              0                                              |
|    Component    |                                              0                                              |
|  Symbolic Name  |                                              0                                              |
|  Message Text   | The response message body was not read  (This may indicate the connection has been closed.) |
  
### Explanation  
 The client may be disconnected before the response message is sent back.  
  
### User Action  
 Check the client connectivity. The steps taken, and the extent of the action, will depend on the port type.   
For further information, see [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).