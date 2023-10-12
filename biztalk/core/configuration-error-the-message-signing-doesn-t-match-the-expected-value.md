---
description: "Learn more about: Configuration error. The message signing doesn&#39;t match the expected value."
title: "Configuration error. The message signing doesn&#39;t match the expected value."
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuration error. The message signing doesn&#39;t match the expected value.
## Details  
  
|       Field          |      Error Details                                                                                                                                                                        |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                              |
| Product Version |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                          |
|    Event ID     |                                                                                      -                                                                                       |
|  Event Source   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                            |
|    Component    |                                                                                  AS2 Engine                                                                                  |
|  Symbolic Name  |                                                                   AS2DecoderPartySigningConfigurationError                                                                   |
|  Message Text   | Configuration error. The message signing doesn't match the expected value. Contact the sending partner and verify signature use. AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not process the AS2 message because signing is specified in the party settings, but the AS2 message is not signed, or signing is specified not to be enabled, but the message is signed.  
  
## User Action  
 To resolve this error, verify that the incoming AS2 message is signed if signing is specified in the party settings or that the incoming AS2 message is not signed if signing is specified as not enabled in the party settings. Do one of the following:  
  
1.  If the **Override inbound message properties** property is selected in the Party as AS2 Message Sender page of the AS2 Properties dialog box in the BizTalk Server Administration Console, the **Message should be signed** property is selected, but the message is not signed, contact the party that sent the message and ask them to sign the message, and resend it. Or you can clear the **Message should be signed** property, or the **Override inbound message properties** property.  
  
2.  If the **Override inbound message properties** property is selected, the **Message should be signed** property is cleared, but the message is signed, contact the party that sent the message and ask them not to sign the message, and resend it. Or you can select the **Message should be signed** property.
