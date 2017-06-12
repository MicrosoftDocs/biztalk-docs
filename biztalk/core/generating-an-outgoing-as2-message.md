---
title: "Generating an Outgoing AS2 Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 288c8101-9a96-4f98-ae18-df43c7cdb3a0
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generating an Outgoing AS2 Message
The AS2EDISend and AS2Send send pipelines generate an outbound message as follows. Each pipeline uses the properties in the one-way agreement tab of the **Agreement Properties** dialog box to generate the outgoing AS2 message.  
  
## Agreement, Destination, and MessageID Determination  
 The AS2 send pipelines determine the agreement and destination to be used in sending an AS2 message as follows:  
  
-   To determine the agreement to use in processing an outgoing message, the AS2 encoder attempts to match the AS2-To properties in the message and the AS2Identity for a party’s business profile, or the send port subscribing to the message with a send port associated with the agreement. For more information on this process, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
-   To determine the destination of the message, the send pipeline in a dynamic send port uses the OutboundTransportLocation property, which must be written or promoted to the context by a backend application for the dynamic send port to work. The send pipeline in a static send pipeline will determine the destination from the AS2-From property in the AS2 agreement properties and the identities of the business profile properties.  
  
-   The AS2 Encoder needs to set the MessageId header of an outgoing AS2 message. The send pipeline determines the MessageId from either the `EdiIntAS.MessageId` context property or the `HTTP.UserHttpHeaders` context property. If both of those context properties are set, the encoder uses the value from the `HTTP.UserHttpHeaders` context property. If neither of them is set, the send pipeline autogenerates a value for MessageID.  
  
## Outgoing Message Processing  
 The steps that the AS2 send pipelines use in processing an outgoing AS2 message are as follows:  
  
-   Makes a copy of the message in native format, and stores the copy in the non-repudiation database, if non-repudiation of AS2 messages is enabled in agreement properties.  
  
-   The AS2 Encoder builds the HTTP (and AS2) headers into the `HTTP.UserHttpHeaders` context property. For more information on this process, see [Send-Side Processing of an Outgoing EDI Message over AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md).  
  
-   Writes `HTTP.UserHttpHeaders` to the context.  
  
-   Compresses the outgoing message, if enabled.  
  
-   Performs MIME processing, including encrypting the message (if enabled in the **Message should be encrypted** agreement property) and applying a digital signature (if enabled in the **Message should be signed** agreement properties). The AS2Send pipeline uses either SHA1 or MD5 to apply the signature, based upon agreement settings.  
  
-   Creates a Content-Disposition MIME header containing the specified value, if transmit file name is enabled in agreement properties.  
  
-   Makes a copy of the encrypted message (in wire format), and stores the copy in the non-repudiation database, if enabled in the **NRR enabled for outbound encoded AS2 messages** in the agreement property.  
  
-   If an MDN is required, computes the MIC value and stores it in the data store.  
  
-   Delivers the message to the HTTP adapter, which writes the headers from the UserHTTPHeaders context property into the outgoing AS2 message.  
  
-   If reliable messaging is required, resends the message until an MDN is received.  
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)   
 [AS2 Send Components](../core/as2-send-components.md)