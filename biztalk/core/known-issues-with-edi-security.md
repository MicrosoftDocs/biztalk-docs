---
title: "Known Issues with EDI Security | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d7f68bc-8460-4656-b9f2-955337458d78
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Security
This topic describes known issues with the security of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.  
  
## BizTalk Will Not Suspend a Signed Message from a Party for which No Certificate is Set  
 If you do not set a signing certificate on a party (in the Certificate node of the party's Party Properties page), but an incoming message from that party is signed, BizTalk Server will not suspend the message and throw an exception based on the absence of the certificate.  
  
 If you override inbound message properties (on the Party as AS2 Message Sender page), and clear the "Message should be signed" property, BizTalk Server will suspend a signed incoming message.  
  
## Access to Program Files Folder Can Be Limited to Prevent File Tampering  
 If the Program Files folder that contains BizTalk Server executables and EDI schemas is available to users who are not authenticated, those users can potentially modify those files. To protect against that threat, you can use Access Control Lists (ACLs) on the Program Files folder to limit access to trusted users.  
  
## A Schema with a Long Field Can Be Susceptible to a Denial-of-Service Attack  
 A custom schema that has a field of very great length could potentially be exploited by a denial-of-service attack. Schemas that are shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have fields with great lengths, and therefore are generally not susceptible to such an attack.  
  
## Message Processing Will Be Aborted If a Control Number Exceeds Its Maximum Length  
 An interchange, group, or transaction set control number has a limited maximum length. If the length of one of these control numbers exceeds the maximum length, the processing of all messages of that encoding type for a single party will be aborted. A message of another encoding type (EDIFACT instead of X12, for example) will not be affected. This could represent a security vulnerability.  
  
 If the length of a sequence number exceeds the maximum length, the user has to reset the sequence number in the EDI Property for the party affected. After the number has been reset, all messages of that encoding type can once again be processed.  
  
 For X12 messages, the maximum length of a control number is nine digits. For EDIFACT message, the maximum length of a control number is 14 digits over three fields.  
  
## Using the EDI Receive Pipeline with an HTTP Adapter Will Leave the Connection Open If No ACK Is Sent  
 A security issue could occur if you create a receive location that uses the EDIReceive pipeline and has a transport type of HTTP. The EdiReceive pipeline will not generate an HTTP "200 OK" acknowledgment. If no EDI acknowledgment is returned, the connection will not be terminated gracefully, but will remain open. The connection will time out when the time-out period has expired.  
  
 This is not an issue with the AS2EdiREceive pipeline.  
  
## An X12-Encoded Message Is Suspended If Port-Based Authentication Is Enabled and BizTalk Server Does Not Have Access to the Authorization and Security Information  
 **Symptom**  
  
 When a message is received over a receive port for which authentication is enabled, and the party that sent the message cannot be determined, BizTalk Server will suspend the message.  
  
 **Possible Cause**  
  
 If authentication is enabled for a receive port (the "No Authentication" property for the receive port is cleared), BizTalk Server requires settings for the "ISA1-2 (Authorization qualifier and information)" and "ISA3-4 (Security qualifier and information)" properties in order to process the interchange. These properties are set for a party in the X12 Interchange Processing Properties page for the party as an interchange sender. If BizTalk Server cannot determine the values of these properties, it will suspend the message.  
  
 This can occur in two ways. In the first case, if BizTalk Server cannot determine the party that sent the message, it will use the EDI global properties and will not have access to the authorization and security settings. As a result, it will suspend the message. In the second case, if BizTalk Server determines the party, but the ISA1-2 and ISA3-4 properties for the party are not configured, BizTalk Server will again not have access to authorization and security information and will suspend the message.  
  
 **Resolution**  
  
 Make sure that the sending party for the message can be identified and that the ISA1-2 and ISA3-4 properties are defined in the party agreement.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)