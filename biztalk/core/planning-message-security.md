---
description: "Learn more about: Planning Message Security"
title: "Planning Message Security"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Planning Message Security
Based on the security policies in your company, you may want to consider the questions in the following table to determine the level of security that you must implement in your BizTalk Server environment. The answers to these questions will determine the security features that you need for messaging.  
  
|Question|BizTalk Server Security Feature|  
|--------------|-------------------------------------|  
|**When receiving a message:**||  
|How do you determine the identity of the sender of the message?|You can use the party resolution component in the BizTalk pipeline and the signing certificate or Windows Security ID (SID) to identify the sender of a message positively. For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).|  
|Do you know the party that sent you the message?|You can use the party resolution component in the BizTalk pipeline to determine whether the party that sent you the message is a trading partner already in your system. For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).|  
|Do you want to avoid receiving messages from parties you do not know?|You can use the authentication required feature in the port to require that BizTalk server processes only the messages from parties that you know. For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).|  
|**When sending a message:**||  
|How do you ensure the privacy of outgoing messages?|You can encrypt the message to ensure that only the intended party can read the message. For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).|  
|How do you prevent malicious users from tampering with the message during transmission?|You can use digital signatures to ensure the integrity of the message. For more information, see [Outbound Message Protection](../core/outbound-message-protection.md).|  
  
## In This Section  
  
-   [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md)  
  
-   [Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md)  
  
-   [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md)  
  
-   [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md)
