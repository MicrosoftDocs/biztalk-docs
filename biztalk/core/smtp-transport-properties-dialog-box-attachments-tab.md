---
title: "SMTP Transport Properties Dialog Box, Attachments Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.smtp.transport.attachments"
helpviewer_keywords: 
  - "properties, SMTP adapters"
  - "send ports, SMTP adapters"
  - "SMTP adapters, properties"
  - "SMTP adapters, send ports"
  - "SMTP adapters, attachments"
ms.assetid: d0bba641-1112-4770-8e85-6e0fe74c0d3f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Transport Properties Dialog Box, Attachments Tab
In the **SMTP Transport Properties** dialog box, use the **Attachments** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remaining BizTalk message parts**|Specify how BizTalk message parts are attached to the e-mail message.<br /><br /> Options:<br /><br /> -   Do not attach parts<br />-   Attach only body part<br />-   Attach all parts<br /><br /> Default value: Do not attach body parts.|  
|**Add**|Specify a file or files to attach to the e-mail message. After clicking the Add button you can browse to select a file and add it to the list of files to be attached.<br /><br /> Maximum path length: 256 characters **Note:**  We recommend as a best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.|  
|**Remove**|Removes the selected file from the list of files to be attached to the e-mail message.|  
  
## See Also  
 [Restrictions on the SMTP To Property](../core/restrictions-on-the-smtp-to-property.md)