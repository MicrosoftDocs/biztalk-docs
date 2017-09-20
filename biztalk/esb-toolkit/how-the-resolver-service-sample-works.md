---
title: "How the Resolver Service Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33b5f886-ec54-4b2b-b09d-fb4c47ad43a5
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the Resolver Service Sample Works
The Resolver Service sample instantiates the Resolver service and passes the message you specify to it for processing. The Resolver Service sample client application uses the first parameter as the path to the ResolverList.xml file, which contains multiple resolver requests, and sends these requests to the Resolver service. For example, the following is the XPATH request used in the sample.  
  
```  
  
//XPATH  
<Resolver>  
  <name>XPATHWithFILE</name>   
  <Content>![CDATA[XPATH:\\TransportLocation=/*[local-name()='OrderDoc'   
    and namespace-uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/']/*[local-name()='ID' and namespace-  
    uri()='http://globalbank.esb.dynamicresolution.com/  
    northamericanservices/'];TargetNamespace=;  
    MessageExchangePattern=;EndpointConfig=;JaxRpcResponse=;TransportType=;  
    Action=;TransformType=]]  
  </Content>   
  <body>  
    ![CDATA[   
    <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
      <ns0:customerName>Microsoft</ns0:customerName>  
  
<ns0:ID>FILE://C:\Projects\Microsoft.Practices.ESB\Source\Samples  
    \DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml</ns0:ID>   
      <ns0:requestType>10</ns0:requestType>   
    </ns0:OrderDoc>  
    ]]   
  </body>  
</Resolver>  
```  
  
> [!NOTE]
>  The actual content of the **\<Content>** element does not contain the white space characters used to wrap the lines in the preceding listing.  
  
 The preceding listing shows that the request contains the resolver configuration connection string within a **\<Content>** element. The **\<body>** element contains the message body.  
  
 The Resolver service uses the **ResolverMgr** class to instantiate a concrete instance of the appropriate resolver, defined by the resolver type in the connection string. In the case of the XPATH request, this is the XPATH resolver.  
  
 Next, the framework creates an instance of the **ResolveProvider** class named ESB.Resolver.XPath to process the request. The client application writes the response message from the Resolver service into the folder named \Source\Samples\ResolverService\Output. The following listing shows the contents of the response.  
  
```  
  
//XPATH  
Resolver.Action =   
Resolver.ActionField =   
Resolver.DocumentSpecName =   
Resolver.DocumentSpecStrongName =   
Resolver.EndpointConfig =   
Resolver.EpmRRCorrelationToken =   
Resolver.FixJaxRpc = False  
Resolver.InboundTransportLocation =   
Resolver.InboundTransportType =   
Resolver.InterchangeId =   
Resolver.IsRequestResponse =   
Resolver.MessageExchangePattern =   
Resolver.MessageType =   
Resolver.MethodName =   
Resolver.OutboundTransportCLSID =   
Resolver.ReceiveLocationName =   
Resolver.ReceivePortName =   
Resolver.Success = False  
Resolver.TargetNamespace =   
Resolver.TransformType =   
Resolver.TransportLocation = FILE://C:\Projects\Microsoft.  
    Practices.ESB\Source\Samples  
\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml  
Resolver.TransportNamespace =   
Resolver.TransportType = FILE  
Resolver.WindowUserField =  
```