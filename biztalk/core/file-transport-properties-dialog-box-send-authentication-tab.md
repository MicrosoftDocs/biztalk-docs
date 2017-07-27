---
title: "File Transport Properties Dialog Box, Send, Authentication Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.send.authentication"
helpviewer_keywords: 
  - "file transport, authenticating"
  - "authenticating, file transport"
  - "file transport, properties"
  - "file transport, configuring"
  - "configuring, file transport"
ms.assetid: f492b49b-13f5-480d-b497-451d69531e98
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Send, Authentication Tab
Use the **Authentication** tab to configure the send port for the File adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use these credentials when host does not have access to network share**|Specify to use alternative credentials when the host instance for the File adapter does not have the necessary rights to a network share. This option is only valid when accessing a network share.<br /><br /> Default Value: False<br /><br /> Type: Boolean|  
|**User name**|Specify the user name that has access to the network share.<br /><br /> Type: String|  
|**Password**|Specify the password for the account that has access to the network share.<br /><br /> Type: String|  
  
## See Also  
 [How to Configure a File Send Port](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9)   
 [Restrictions on the File Mask and File Name Properties](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769)   
 [Restrictions on Using Macros in File Names](http://msdn.microsoft.com/library/ac60829d-b076-4630-aea5-a59b32d6250f)