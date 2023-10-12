---
description: "Learn more about: WCF Send Adapter"
title: "WCF Send Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# WCF Send Adapter
The WCF send adapter enables you to call a WCF service through the typeless contract.  
  
## Specifying the WCF Message Body  
 The message body that needs to be sent from BizTalk Server can be inserted into the SOAP message by using one of the following options:  
  
- Extract the content of the BizTalk message body  
  
- Specify the content by using the template  
  
  You can configure these options in the send port transport properties dialog box.  
  
#### Extract the Content of the BizTalk Message Body  
 When this option is selected, the content of the BizTalk message body is inserted into the SOAP Body element for the outbound WCF message body.  
  
#### Specify the Content by Using the Template  
 When this option is selected, the BizTalk message body is placed in the SOAP body element under the given XML template for the outbound WCF message body.  
  
## Serializing the BizTalk Message into a SOAP Message  
 The send adapter serializes the BizTalk message into a SOAP message before sending it out. The following rules apply during serialization of the message:  
  
-   If the BizTalk message is a multipart message, then only the body part is used.  
  
-   If the BizTalk message contains the entire SOAP envelope, then it is wrapped into another SOAP envelope.  
  
-   If the BizTalk message contains arbitrary XML data, then the BizTalk message is placed into the SOAP Body element.  
  
## Handling Web Services Headers  
 During send operations BizTalk Server does not have control over Web services standard headers. Those headers are set and processed by the WCF. The only standard header that can be modified by the BizTalk Server application is the **a:Action** header. If the context property **Action** is specified on the adapter namespace, then the WCF send adapter will use the value of the property to set the **Action** on the SOAP message.  
  
> [!NOTE]
>  For dynamic send ports, if **Action** is specified in the **OutboundHeaders**, the context property you set for the **WCF.Action** will be ignored.  
  
## Specifying the BTS.IsDynamicSend Context Property  
 The WCF send adapter caches the configuration for send ports. If the **BTS.IsDynamicSend** property is set to true, the WCF send adapter does not use the cached configuration, but instead reads all configuration information from the message context properties of the outbound messages. On a static send port, the WCF send adapter uses **BTS.SPLastUpdatedTime**, which is the time that the static send port settings were last modified, to detect if there are any configuration changes on the static send port. In this way the WCF send adapter does not need to read all of the settings from every message context.  
  
 If you want to override the static send port properties other than the **WCF.Action** property in a send pipeline, you need to set the **BTS.IsDynamicSend** property to true so that the WCF send adapter will not use the cached configuration even though the last updated timestamp has not changed.  
  
## See Also  
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF Receive Adapter](../core/wcf-receive-adapter.md)   
 [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md)   
 [How to Use Message Context Properties](../core/how-to-use-message-context-properties.md)
