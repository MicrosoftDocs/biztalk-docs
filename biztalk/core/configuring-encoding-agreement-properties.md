---
title: "Configuring Encoding Agreement Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.ediagreement.properties"
ms.assetid: 0cb1146e-177c-42fa-b1d8-a834229c2af9
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Encoding Agreement Properties
A Trading Partner Agreement (TPA) is a definitive and binding agreement between two trading partners for transacting messages over a specific B2B Protocol. In simpler terms, a TPA is an understanding between two business profiles to use a specific message encoding protocol (X12 or EDIFACT) or a specific transport protocol (AS2) while exchanging B2B messages with each other. In addition to agreeing upon the encoding and transport protocol, an agreement can be used to customize how the messages will be formed and delivered.  
  
- As part of the encoding protocol settings, you can also define whether the sending party expects an acknowledgement, whether the messages will be batched or sent individually, etc.  
  
- As part of the transport protocol settings, you can also define whether the message should be signed, whether the message should be encrypted, etc.  
  
  > [!NOTE]
  >  For more information about transport protocol (AS2) settings, see [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).  
  
  You must make the following considerations while creating an agreement:  
  
- A trading partner agreement between two parties is bi-directional. A single agreement between two parties (Party A and Party B) can be used to send messages from Party A to Party B and also to receive messages from Party B to Party A. To represent a bi-directional agreement in the user interface, each one-way agreement is represented in a single tab. So, in the agreement user interface, you will see two tabs, **PartyA->PartyB** (representing the one-way agreement for messages sent from Party A to Party B) and **PartyB->PartyA** (representing the one-way agreement for messages sent from PartyB to PartyA.)  
  
- Each one-way agreement caters to one end-to-end message transaction. Sending or receiving acknowledgements is also part of the same message transaction and hence should be configured on the same one-way agreement tab. For example, consider Party A sends an EDI interchange to Party B and in response, Party B sends an acknowledgement back to Party A. So, all the properties related to sending an interchange and expecting an acknowledgement must be set on the **PartyA->PartyB** tab.  
  
  > [!NOTE]
  >  Even though the acknowledgement is part of the same message transaction, the properties related to how the acknowledgement should be generated are configured in the **PartyB->PartyA** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **PartyA->PartyB** tab. For example, if sender and receiver identifiers are set to THEM and US in the agreement to which the interchange message resolved to, the sender and receiver context properties will be set to US and THEM in the acknowledgement. Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to US and THEM respectively. Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked. So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **PartyB->PartyA** tab.  
  >   
  >  Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties. However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.  
  
- You can have an encoding agreement (to define the message encoding to be used for the messages) and a transport agreement (to define the transport protocol to be used for exchanging messages). Having an encoding agreement is mandatory. The parties may choose to have an AS2 agreement only if they want to use the AS2 protocol to transfer messages. For example, an AS2 agreement is not required if the two parties choose to transfer messages over e-mail.  
  
  > [!NOTE]
  >  For more information about AS2 agreement, see [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).  
  
## In This Section  
  
-   [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md)  
  
-   [Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md)