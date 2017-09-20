---
title: "Processing Multi Part Messages with the POP3 Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56ad041f-f155-4c1c-ab87-1405c80d9b68
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing Multi Part Messages with the POP3 Adapter
The POP3 Adapter can process MIME-encoded messages that conform to the IETF standards documented in [RFC 2045](http://go.microsoft.com/fwlink/?LinkId=58810), [RFC 2046](http://go.microsoft.com/fwlink/?LinkId=58811), and [RFC 2047](http://go.microsoft.com/fwlink/?LinkId=58812). MIME encoded messages can have from one to many parts with different content types. This topic discusses the how the POP3 adapter processes multi part MIME encoded messages.  
  
## Receiving Multi part Messages with the POP3 Adapter  
 If a receive location that uses the POP3 adapter has the **Apply MIME Decoding** option set to **True** then the POP3 adapter performs the following actions when receiving a MIME-encoded message:  
  
1.  Creates a multi part BizTalk message from the parts of the MIME encoded message that it receives. This multi part message can contain from 1 to many parts and will contain the same number of parts as the MIME encoded message that is received.  
  
2.  Scans the headers of the MIME encoded message. If any headers match the list of properties documented in the topic [POP3 Adapter Property Schema and Properties](../core/pop3-adapter-property-schema-and-properties.md) then these headers are promoted to the multi part BizTalk message as context properties.  
  
3.  Uses a configurable algorithm to designate one of the parts of the MIME encoded message as the BizTalk message body part. The algorithm used to determine which message part will be the BizTalk message body part is described below in the section **Body Part Selection Algorithm Used by the POP3 Adapter**.  
  
4.  Publishes the multi part BizTalk message to the MessageBox.  
  
## Body Part Selection Algorithm Used by the POP3 Adapter  
 When the POP3 adapter creates a multipart BizTalk message from the parts of the MIME-encoded message that it receives, it selects one of the message parts as the BizTalk message body part. The BizTalk message body part is used by BizTalk Server for things such as message validation, mapping, property promotion, flat file assembly and other operations. Subscribers to a multi part BizTalk message receive all of the message parts but will only consume the designated BizTalk message body part unless using an orchestration, a custom pipeline, or an adapter that can understand multi part messages. For example, you can configure an orchestration to read all parts of multi part message; the SMTP adapter can read all of the parts of a multi part message, and a custom pipeline can be configured to use the MIME/SMIME encoder pipeline component. For more information about using an orchestration to consume a multi part message see the section below, **Processing Multi Part Messages in Orchestrations**.  
  
 The POP3 adapter selects the BizTalk message body part from the available body parts based upon the values supplied for the **Body Part Index** and the **Body Part Content Type**.  
  
> [!NOTE]
>  The POP3 adapter is designed to recognize the Body Part Content Types that are defined in [RFC 2046](http://go.microsoft.com/fwlink/?LinkId=119569).  
  
 The algorithm that is used to select the BizTalk message body part of an e-mail is described below:  
  
1.  If the **Body Part Index** is set to 0 and the **Body Part Content Type** is blank then the following algorithm is used to select the BizTalk message body part:  
  
    -   Use the first MIME part with the Content-Description header set to "body".  
  
    -   Otherwise use the first MIME part with the Content-Type header set to "text/xml".  
  
    -   Otherwise use the first MIME part with the Content-Type header set to "text/plain".  
  
    -   Otherwise use the first MIME part with the Content-Type header set to "text/".  
  
    -   Otherwise use the first MIME part.  
  
2.  Otherwise if the **Body Part Index** is set to 0 and the **Body Part Content Type** is set, then the first body part of the incoming message that matches the specified **Body Part Content Type** is selected as the BizTalk message body part. If there are no parts with a matching content type then the message is suspended.  
  
3.  Otherwise if the **Body Part Index** is set to a value greater than 0 and the **Body Part Content Type** is blank, then the body part with the specified index is selected as the BizTalk message body part. If the specified index is greater than the number of body parts then the message is suspended.  
  
4.  Otherwise if the **Body Part Index** is set to a value greater than 0 and the **Body Part Content Type** is set, then the **Body Part Index** is only applied to those body parts that match the specified **Body Part Content Type** and the corresponding body part is selected as the BizTalk message body part. If the specified index is greater than the number of parts with a matching content type then the message is suspended. If there are no parts with a matching content type then the message is suspended.  
  
5.  The part that is selected as the BizTalk message body part becomes the first part of the multi part BizTalk message that is published to the MessageBox, the remaining parts of the message maintain the order that they had in the original MIME encoded message.  
  
## Processing Multi Part Messages in Orchestrations  
 When the POP3 adapter creates a multi part BizTalk message from a MIME encoded message that it receives, all of the parts are published to the MessageBox database even though only one of the parts is designated as the BizTalk message body part. These parts can be subsequently consumed by an orchestration that subscribes to the multi part message. This section documents some considerations when processing multi part messages in an orchestration.  
  
### Processing multi part messages with a known number of parts and known part types  
 If your orchestration is receiving a multi part message with a known number of parts and known part types then you can declare a multi part message in the orchestration and set the number of parts and part types at design time.  
  
### Processing multi part messages with unknown part types  
 If your orchestration is receiving a multi part message with unknown part types then you can declare a multi part message in the orchestration and use the **XmlDocument** type for each of the parts for which the type is unknown.  
  
### Processing multi part messages with an unknown number of parts and all of the part types are unknown  
 If your orchestration is receiving a multi part message with an unknown number of parts then you can declare a multi part message with a single part of the **XmlDocument** type in the orchestration to receive the message. If a multi part message that contains greater than the number of declared parts is received, the orchestration engine reads how many parts there are in the message, then constructs the proper part types for the parts that match the number of parts in the declared message type and then constructs **XmlDocument** parts for the remaining parts.