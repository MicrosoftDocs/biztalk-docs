---
title: "WCF-Custom Transport Properties Dialog Box, Send, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.send.general"
helpviewer_keywords: 
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
ms.assetid: dd6f0eae-eb8b-4e1c-ad92-e101942fc0b1
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Send, General Tab
Use the **General** tab to configure the endpoint address, the service identity, and the SOAP **Action** feature for the WCF-Custom send port. The WCF-Custom adapter enables the use of Windows Communication Foundation (WCF) extensibility features. The adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location and send port.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the fully qualified URI of the destination service for this send port. The available transport scheme for this property is decided by the **Binding Type** property on the **Binding** tab. **Note:**  You can also import and export this property through the **Import/Export** tab. <br /><br /> Maximum length: 255<br /><br /> The default is an empty string.|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. **Note:**  You can also import and export this property through the **Import/Export** tab. If the send port is configured to use multiple identity types, only the identity type with the lowest number can be exported. For example, if **1. DNS** and **4. RSA** are both set in the **Identity Editor** dialog box, only the **1. DNS** property is saved by using the **Export** tab. <br /><br /> The default value is cleared.|  
|**Action**|Required. Specify the **SOAPAction** header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /><br /><br /> \</BtsActionMapping><br /><br /> If outgoing messages comes from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)   
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)