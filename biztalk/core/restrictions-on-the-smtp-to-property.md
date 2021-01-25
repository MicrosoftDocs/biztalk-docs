---
description: "Learn more about: Restrictions on the SMTP To Property"
title: "Restrictions on the SMTP To Property | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [SMTP adapters], restrictions"
  - "SMTP adapters, restrictions"
ms.assetid: c876d30e-44ab-462d-8c98-64416ed6dd1f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restrictions on the SMTP To Property
The **To** property is a string that specifies the SMTP address of the recipient of the message. You can list several addresses with a separator that SMTP server supports.  
  
 There are no specific restrictions for the format of an SMTP address. This means that the adapter will accept any format that an SMTP server supports. If a user provides addresses that are not valid, the send operation will fail and the SMTP send adapter will report an error.  
  
 The only restrictions for this property are that it must not be empty and its size must not exceed 256 characters.  
  
## See Also  
 [Restrictions When Configuring the SMTP Adapter](../core/restrictions-when-configuring-the-smtp-adapter.md)
