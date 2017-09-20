---
title: "Run Operations on Business Components with the Siebel adapter using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, perform operations using the channel"
  - "performing operations, using the channel"
ms.assetid: bae74013-38fa-413c-ba91-4e4ba096339e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run Operations on Business Components with the Siebel adapter using the WCF Channel Model
This section demonstrates how to perform operations on Siebel using the channel created in [Create a Channel using Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).  
  
```  
// create binding  
SiebelBinding binding = new SiebelBinding();  
  
//set up an endpoint address  
EndpointAddress address = new EndpointAddress("siebel://Username=myuser;Password=mypass@mysiebelserver:1234?SiebelObjectManager=SSEObjMgr&SiebelEnterpriseServer=ent771&Language=enu");  
  
//create request channel factory  
IChannelFactory<IRequestChannel> factory = binding.BuildChannelFactory<IRequestChannel>(new BindingParameterCollection());  
  
//open factory  
factory.Open();  
  
//create request channel using endpoint  
IRequestChannel channel = factory.CreateChannel(address);  
  
//open the channel  
channel.Open();  
  
// send request message and receive reply  
System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create(inputXml);  
System.ServiceModel.Channels.Message messageIn = System.ServiceModel.Channels.Message.CreateMessage(MessageVersion.Default,action,readerIn);  
System.ServiceModel.Channels.Message messageOut = channel.Request(messageIn);  
  
// get response XML from SOAP message  
System.Xml.XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
// save output file  
XmlDocument doc = new XmlDocument();  
doc.Load(readerOut);  
doc.Save(outputXml);  
Console.WriteLine("XML written out to {0}", outputXml);  
  
// close the channel and the factory  
channel.Close();  
factory.Close();  
```  
  
## See Also  
 [Develop Siebel Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)   
 [Run Operations on Business Components with the Siebel adapter Using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)