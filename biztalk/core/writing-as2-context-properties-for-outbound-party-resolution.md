---
description: "Learn more about: Writing AS2 Context Properties for Outbound Party Resolution"
title: "Writing AS2 Context Properties for Outbound Party Resolution"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Writing AS2 Context Properties for Outbound Party Resolution
Agreement resolution of outbound AS2 message can be performed using the AS2To context property or the AS2To property in the `Http.UserHttpHeaders` context property. However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write the AS2To property to the context upon receiving an AS2 message. If you want to perform agreement resolution on the AS2To or UserHttpHeaders context property, you have to write a custom orchestration or a custom pipeline component to do so. This is required only if the send port is not linked to the agreement.  
  
 In a custom orchestration, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code:  
  
```  
Message_1(Http.UserHttpHeaders) = “AS2-To: MyPartner\r\n” + Message_1(Http.UserHttpHeaders);  
```  
  
 In a custom pipeline component, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code. You need to append AS2-To to `Http.UserHttpHeaders` context property before the message is processed by the As2Encoder component.  
  
```  
string strName="UserHttpHeaders";  
string strValue = "AS2-To: MyPartner\r\n" + (string)baseMessage.Context.Read(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties");  
baseMessage.Context.Write(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties", strValue);  
```  
  
 For more information on promoting the `EDIIntAS.AS2To` property or the `BTS.UseHttpHeaders` property to the context, see "Promoting AS2 Header Context Properties" in the [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
 For code that you can add to a custom pipeline component to write the headers from the HTTP.UserHttpHeaders context property into the message, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
## See Also  
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)
