---
title: "Configuring Dynamic Send Ports Using WCF Adapters Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF services, send ports"
  - "send ports, WCF services"
  - "dynamic send ports, WCF services"
  - "send ports, dynamic"
ms.assetid: 2a7e2cd2-fa2d-45da-bb8e-eb8bab21bfa3
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Dynamic Send Ports Using WCF Adapters Context Properties
You can configure dynamic send ports for WCF adapters. The URI, action, and binding might be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following WCF-NetTcp adapter:  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.SecurityMode)="Transport";  
MessageOut(WCF.TransportClientCredentialType)="Windows";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/netTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-NetTcp";  
```  
  
 The following code shows an example of how to specify the WCF context properties in the **Expression** shape for a WCF-Custom adapter:  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.BindingType)="customBinding";  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.BindingConfiguration)=@"<binding name=""customBinding""><binaryMessageEncoding /><tcpTransport /></binding>";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/customNetTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
 Considerations when specifying WCF context properties are as follows:  
  
- There are addresses that can be mapped to multiple adapters. For example, an address that starts with http:// or https:// can be handled by the HTTP adapter as well as by the WCF-BasicHttp, WCF-WsHttp, or WCF-Custom adapters. For another example, in the above sample code, both of them are using the address starts with net.tcp://, yet because the second sample code uses custom binding, WCF-Custom adapter should be used to handle the address. Therefore, to identify the correct adapter, you must configure the optional **Microsoft.XLANGs.BaseTypes.TransportType** field in an **Expression** shape with the adapter that you want to use.  
  
  > [!NOTE]
  >  If the address starts with http:// or https://, and if you do not specify the **Microsoft.XLANGs.BaseTypes.TransportType** field, by default, the BizTalk engine will use the HTTP adapter.  
  
- The **WCF.BindingType** identifies the binding by name. It can be one of the following:  
  
  - basicHttpBinding  
  
  - customBinding  
  
  - netMsmqBinding  
  
  - netNamedPipeBinding  
  
  - netTcpBinding  
  
  - wsFederationHttpBinding  
  
  - wsHttpBinding  
  
    The above list can be extended. For example, you can add your own binding to it such as FtpBinding.  
  
- The **WCF.BindingConfiguration** specifies the binding configuration for the binding type. It takes any binding that are registered in the machine configuration file. It also takes the XML configuration in the same format as used in the binding configuration in the WCF configuration file.  
  
- You may need to specify additional WCF properties. You can type **WCF** in the Expression Editor, and the IntelliSense feature should list all the available context properties. For more information about WCF context properties, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).  
  
  The preceding examples show how to configure **WCF.Action** with a single action. For multiple actions mapping scenarios, WCF adapter do not support using multiple actions mapping with dynamic send ports. You can just set the actual action in the **WCF.Action** context property as showing in above.  
  
## See Also  
 [Specifying SOAP Actions for WCF Send Adapters](../core/specifying-soap-actions-for-wcf-send-adapters.md)   
 [How to Use Expressions to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)   
 [Port Bindings](../core/port-bindings.md)