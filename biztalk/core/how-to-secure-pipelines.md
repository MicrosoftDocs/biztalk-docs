---
title: "How to Secure Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3a717f-acf8-4f08-a6fb-6d1d48b5b80a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Secure Pipelines

## Authentication trusted
Hosts can be marked in the administration console as **Authentication Trusted**. Denoting a host as Authentication Trusted means that the Microsoft BizTalk Server will trust the security-related properties sent on the message context of a message from that host. The security-related properties on the message context are the **OriginatorPID**, which corresponds to the message context property BTS.SourcePartyID, and the **OriginatorSID**, which corresponds to the message context property **BTS.WindowsUser**. For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 A host that is marked as **Authentication Trusted** is allowed to indicate that the trusted host is adding a message to the queue from someone other than itself as the sender of the message. In other words, hosts that are not marked as **Authentication Trusted** are not allowed to add a message to the queue from a message sender other than themselves.  
  
> [!IMPORTANT]
>  The MIME/SMIME Decoder pipeline component does not check the expiration date of decryption certificates. However, it does check the expiration date of signing certificates.  
  
 For information about encoding and decoding messages sent over SMTP or HTTP, see [MIME-SMIME Encoder Pipeline Component](../core/mime-smime-encoder-pipeline-component.md). Also see [MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md).  
  
 For information about signature verification when dealing with third parties, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md). Also see [How to Create an Agreement](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).  
  
## See Also  
 [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md)   
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)