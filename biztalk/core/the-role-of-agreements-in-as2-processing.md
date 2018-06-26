---
title: "The Role of Agreements in AS2 Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb6a6fe1-8fb4-4998-a1b4-aadad7e672c4
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Role of Agreements in AS2 Processing
An organization uses [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive AS2 messages from, and send AS2 messages to, one or more trading partners. The trading partners, in turn define business profiles that are business entities within an organization. You set AS2 properties in bi-directional trading partner agreements between two business profiles belonging to different trading partners.  
  
 You can create trading partner agreements in the Trading Partner Management (TPM) user interface. The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
 For more information about how trading partners, business profiles, and agreements tie together into a TPM solution, see [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
## Configuring an Agreement for AS2 Processing  
 Any time a trading partner receives an AS2 message from, or sends an AS2 message to, another trading partner, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] AS2 receive pipeline or AS2 send pipeline will process the message according to the AS2 agreement properties between the two trading partners. You can configure the AS2 properties that define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform AS2 communications, both incoming and outgoing.  
  
> [!NOTE]
>  Unlike in EDI processing, there are no fallback AS2 agreements that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement. The AS2 receive or send pipeline will process the message only if an agreement is determined.  
> 
> [!NOTE]
>  The AS2 agreement is configured separately from the EDI agreement. When receiving documents, the AS2 agreement is resolved during AS2 processing, then the EDI agreement is resolved separately during EDI processing. Both the agreements together make a partnership. For more information see [Trading Partner Agreement](../core/trading-partner-agreement.md).  
> 
> [!NOTE]
>  Properties that define general aspects of the party, such as name and aliases, send ports, and signing certificate are specified as part of the trading partner’s properties.  
  
 You can use HTTP/HTTPS transport for either EDIINT/AS2-encoded messages or non-EDI over AS2-encoded messages. If you transmit EDIINT/AS2-encoded messages over HTTP/HTTPS transport, the EDI properties for the agreement will apply.  
  
 The signing certificate for the home organization is defined in the **Certificate** page of the **BizTalk Group - Group Properties** dialog box. Additionally, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to override the default signing certificate for AS2 messages by defining a certificate as part of the agreement properties.  To define a different certificate for a specific agreement, use the **Signature Certificate** page of the one-way AS2 agreement in the **Agreement Properties** dialog box. For instructions on how to specify a different certificate, see [Configuring Signature Certificates (AS2)](../core/configuring-signature-certificates-as2.md).  
  
## Determining an Agreement for AS2 Processing  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an AS2-encoded message, it attempts to determine the party that sent the message by matching the AS2-From header to the AS2-From agreement settings in the one-way agreement for the party. When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends an AS2-encoded message, it attempts to determine the party that will receive the message by matching the AS2-To header to the AS2-To agreement property in the one-way agreement for the party. For more information, see [Agreement Resolution for Incoming AS2 Messages](../core/agreement-resolution-for-incoming-as2-messages.md) or [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
## See Also  
 [Agreement Resolution for Incoming AS2 Messages](../core/agreement-resolution-for-incoming-as2-messages.md)   
 [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md)   
 [Configuring AS2 Properties](../core/configuring-as2-properties.md)