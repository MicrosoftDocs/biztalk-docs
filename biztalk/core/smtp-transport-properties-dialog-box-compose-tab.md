---
title: "SMTP Transport Properties Dialog Box, Compose Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.smtp.transport.compose"
helpviewer_keywords: 
  - "properties, SMTP adapters"
  - "send ports, SMTP adapters"
  - "SMTP adapters, properties"
  - "SMTP adapters, send ports"
ms.assetid: 2bfd6bf6-9cce-4c28-a53d-c93efef30c83
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Transport Properties Dialog Box, Compose Tab
In the **SMTP Transport Properties** dialog box, use the **Compose** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.  
  
|**Use this**|**To do this**|  
|------------------|--------------------|  
|**BizTalk message body part**|Specify to use the BizTalk message body part for the body of the e-mail being sent.|  
|**Text**|Specify text to be used for the body of the e-mail being sent. Once the Text option is selected you can enter the text for the e-mail body into the text box.<br /><br /> Maximum Length: 64Kb|  
|**Charset for the text**|Specify the character set to use for encoding the body of the e-mail being sent. This option is only available if the Text option is selected.<br /><br /> Default value: UTF-8 (65001)|  
|**File**|Specify that the contents of a file will be used for the body of the e-mail being sent and specify the path to the file. Once the File option is selected you can click the Ellipses button (…) to browse to the file.<br /><br /> Maximum path length: 256 characters **Note:**  We recommend as a best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.|  
|**Charset of the file**|Specify the character set of the contents of a file that will be used for encoding the body of the e-mail being sent. This option is only available if the File option is selected.<br /><br /> Default value: UTF-8 (65001)|  
  
## See Also  
 [Restrictions on the SMTP To Property](../core/restrictions-on-the-smtp-to-property.md)