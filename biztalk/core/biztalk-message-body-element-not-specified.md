---
description: "Learn more about: BizTalk message body element not specified"
title: "BizTalk message body element not specified"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BizTalk message body element not specified
## Details  
  
| Field       |                                  Error Details                                             |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                     BizTalk message body element not specified                     |
  
## Explanation  
 This error indicates the use of the template option for the outbound WCF message. However, the template expression doesn’t contain the BizTalk message body element.  
  
## User Action  
 Ensure that the template expression contains the following element: `<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="[xml|base64|hex|string]"/>`.
