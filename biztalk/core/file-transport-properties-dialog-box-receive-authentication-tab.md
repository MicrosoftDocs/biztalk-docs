---
title: "File Transport Properties Dialog Box, Receive, Authentication Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.receive.authentication"
helpviewer_keywords: 
  - "file transport, authenticating"
  - "authenticating, file transport"
  - "file transport, properties"
  - "file transport, configuring"
  - "configuring, file transport"
ms.assetid: 0e8cb45b-43e7-4ff2-bbd0-c3328f79b629
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Receive, Authentication Tab
Use the **Authentication** tab to configure the receive location for the File adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use these credentials when host does not have access to network share**|Specify to use alternative credentials when the host instance for the File adapter does not have the necessary rights to a network share. This option is only valid when accessing a network share.<br /><br /> Default Value: False<br /><br /> Type: Boolean|  
|**User name**|Specify the user name that has access to the network share.<br /><br /> Type: String|  
|**Password**|Specify the password for the account that has access to the network share.<br /><br /> Type: String|  
  
## See Also  
 [How to Configure a File Receive Location](http://msdn.microsoft.com/library/09736a30-885b-4ecf-a2e0-0f9d064e4ee6)   
 [Restrictions on the File Mask and File Name Properties](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769)