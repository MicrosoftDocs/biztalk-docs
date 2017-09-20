---
title: "POP3 Adapter Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, POP3 adapters"
  - "Subject properties [POP3 adapters]"
  - "Date properties [POP3 adapters]"
  - "From properties [POP3 adapters]"
  - "To properties [POP3 adapters]"
  - "POP3 adapters, properties"
  - "configuring [POP3 adapters], schemas"
  - "configuring [POP3 adapters], properties"
  - "CC properties [POP3 adapters]"
  - "Headers properties [POP3 adapters]"
  - "ReplyTo properties [POP3 adapters]"
  - "DispositionNotificationTo properties [POP3 adapters]"
ms.assetid: 7a10ae1f-dbcf-4c05-9a50-2503895960f9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# POP3 Adapter Property Schema and Properties
The following table lists the properties in the POP3 adapter property schema.  
  
 **Namespace:** http://schemas.microsoft.com/BizTalk/2003/pop3-properties  
  
|**Name**|**Type**|**Description**|  
|--------------|--------------|---------------------|  
|**Subject**|xs:string|Specifies the content placed on the **Subject** header for the message|  
|**From**|xs:string|Specifies the e-mail address placed on the **From** header field of the e-mail message.|  
|**To**|xs:string|Specifies the e-mail address or addresses placed on the **To** header field of the e-mail message.|  
|**ReplyTo**|xs:string|Specifies the e-mail address placed on the **ReplyTo** header field of the e-mail message.|  
|**CC**|xs:string|Specifies the e-mail address or addresses placed on the **CC** header field of the e-mail message.|  
|**Date**|xs:string|Specifies the content placed on the **Date** header field of the e-mail message.|  
|**DispositionNotificationTo**|xs:string|Specifies the content placed on the **DispositionNotificationTo** header field of the e-mail message.|  
|**Headers**|xs:string|Specifies the content of all of the header fields of the e-mail message.|  
  
## See Also  
 [Configuring the POP3 Adapter](../core/configuring-the-pop3-adapter.md)