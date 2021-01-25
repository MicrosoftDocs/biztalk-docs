---
description: "Learn more about: SMTP Adapter Property Schema and Properties"
title: "SMTP Adapter Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UserName property, SMTP adapters"
  - "EmailBodyTextCharset property [SMTP adapters]"
  - "configuring [SMTP adapters], properties"
  - "Subject property [SMTP adapters]"
  - "EmailBodyFileCharset property [SMTP adapters]"
  - "Attachments property [SMTP adapters]"
  - "SMTP adapters, schemas"
  - "EmailBodyText property [SMTP adapters]"
  - "configuring [SMTP adapters], schemas"
  - "CC property [SMTP adapters]"
  - "ReadReceipt property [SMTP adapters]"
  - "Password property [SMTP adapters]"
  - "ReplyBy property [SMTP adapters]"
  - "DeliveryReceipt property [SMTP adapters]"
  - "SMTP adapters, properties"
  - "SMTPAuthenticate property [SMTP adapters]"
  - "EmailBodyFile property [SMTP adapters]"
  - "schemas, SMTP adapters"
  - "SMTPHost property [SMTP adapters]"
  - "From property [SMTP adapters]"
  - "MessagePartsAttachments property [SMTP adapters]"
ms.assetid: 6d062fb6-d728-4525-8f0d-bd3f0f8ff7ca
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Adapter Property Schema and Properties
The following table lists the properties in the SMTP adapter property schema.  
  
 **Namespace:** http://schemas.microsoft.com/BizTalk/2003/smtp-properties  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**Username**|xs:string|Specify the user name to use for authentication with the SMTP server.|  
|**Password**|xs:string|Specify the password to use for authentication with the SMTP server.|  
|**SMTPHost**|xs:string|Specify the name of the SMTP server to use when sending messages.|  
|**From**|xs:string|Specify the e-mail address to place on the SMTP **From** header.|  
|**CC**|xs:string|Specify the e-mail address to send a copy of the message.|  
|**Subject**|xs:string|Specify the subject header for the message.|  
|**SMTPAuthenticate**|xs:int|Specify the type of authentication to use with the SMTP server.|  
|**ReadReceipt**|xs:boolean|Specify whether to send a confirmation e-mail message when the message is read.|  
|**DeliveryReceipt**|xs:boolean|Specify whether to send a confirmation e-mail message after delivery of the message.|  
|**EmailBodyText**|xs:string|Specify text to be used for the body of the e-mail being sent.|  
|**EmailBodyTextCharset**|xs:string|Specify the character set to use for encoding the body of the e-mail being sent when the **EmailBodyText** option is used. The SMTP adapter will convert the **EmailBodyText** to the character set specified by **EmailBodyTextCharset**.|  
|**EmailBodyFile**|xs:string|Specifies that the contents of a file will be used for the body of the e-mail being sent and the full path to the file. This path must be accessible to the host for the SMTP adapter at run time.|  
|**EmailBodyFileCharset**|xs:string|Specify the character set to use for encoding the body of the e-mail being sent if the **EmailBodyFile** property is set. The SMTP adapter will not perform any conversion on the file; the file must already be encoded in this character set. If the file has a Byte-Order-Mark (BOM), the SMTP adapter will remove it.|  
|**Attachments**|xs:string|Specifies that a file or files will be attached to the e-mail message and the full path to the file or files. The specified path or paths must be accessible to the host for the SMTP adapter at run time.|  
|**MessagePartsAttachments**|xs:unsignedInt|Specify how BizTalk message parts are attached to the e-mail message.|  
|**ReplyBy**|xs:dateTime|Specify a dateTime value for the **Reply-To** header in the outgoing e-mail message.|  
  
## See Also  
 [Configuring the SMTP Adapter](../core/configuring-the-smtp-adapter.md)
