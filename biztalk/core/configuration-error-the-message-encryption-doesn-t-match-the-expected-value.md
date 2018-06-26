---
title: "Configuration error. The message encryption doesn&#39;t match the expected value | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99c37c7d-6654-4004-8345-9d7bfc3659b6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration error. The message encryption doesn&#39;t match the expected value
## Details  
  
|                 |                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                |
| Product Version |                                                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                            |
|    Event ID     |                                                                                        -                                                                                         |
|  Event Source   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                              |
|    Component    |                                                                                    AS2 Engine                                                                                    |
|  Symbolic Name  |                                                                   AS2DecoderPartyEncryptionConfigurationError                                                                    |
|  Message Text   | Configuration error. The message encryption doesn't match the expected value. Contact the sending partner and verify encryption use. AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because encryption is specified in the party settings, but the AS2 message is not encrypted, or encryption is specified not to be enabled, but the message is encrypted.  
  
## User Action  
 To resolve this error, verify that the incoming AS2 message is encrypted if encryption is specified in the party settings or that the incoming AS2 message is not encrypted if encryption is specified as not enabled in the party settings. Do one of the following:  
  
1.  If the **Override inbound message properties property is selected** in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be encrypted** property is selected, but the message is not encrypted, contact the party that sent the message and ask them to encrypt the message, and resend it. Or you can clear the **Message should be encrypted** property, or the **Override inbound message properties** property.  
  
2.  If the **Override inbound message properties** property is selected, the **Message should be encrypted** property is cleared, but the message is encrypted, contact the party that sent the message and ask them not to encrypt the message, and resend it. Or you can select the **Message should be encrypted** property.