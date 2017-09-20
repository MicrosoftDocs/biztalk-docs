---
title: "Running the Header Property Access from an Orchestration Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2059eb2c-50a3-4618-a6ec-faa1a9e5d368
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Header Property Access from an Orchestration Sample
This part of the sample demonstrates how the ESB promotes JMS header metadata into message context properties, which code and components in orchestrations within Microsoft BizTalk can access. The sample includes a receive pipeline that contains an instance of the ESB JMS component that promotes JMS header metadata into message context properties.  
  
 The receive port passes the message to an orchestration named JMSRouter that retrieves the queue name assigned by the RfhUtil utility (and sent in the header metadata) from the context properties of the message. The orchestration assigns this queue name to a dynamic send port and sends the message to that port.  
  
 A send pipeline for the port contains an instance of the ESB JMS component that demotes the message context properties into the JMS header metadata.  
  
 **To run the Header Property Access sample**  
  
1.  If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.  
  
2.  Run the IBM RfhUtil utility; select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager, as in Part 1 of this sample.  
  
3.  In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK.  
  
4.  Click the **ReadFile** button in the RfhUtil utility, and then navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\. This file contains a batch of 128 test messages, but the utility loads only the first one.  
  
5.  Click the **RFH** tab, and then make sure that only the **JMS** check box is selected.  
  
6.  Click the **jms** tab, and then make sure that the selected **Reply To** queue is ESB.JMS.SAMPLE.REPLY and that the selected **Destination Queue** is ESB.JMS.SAMPLE.DYNAMICQ2.  
  
7.  Click the **Main** tab, and then click the **Write Q** button to write the message into the queue.  
  
8.  After a delay while the application executes, the ESB output message appears in the ESB.JMS.SAMPLE.DYNAMICQ2 queue. Open the WebSphere Queue Explorer and browse the queues to confirm this.  
  
## How the Sample Works  
 Inside the orchestration, code can access the values that were in the JMS headers by loading the message into an **XmlDocument** instance, as shown in the following code.  
  
```csharp  
if (null != InboundMsg(  
    Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData))  
{     
  jmsInfo.LoadXml(InboundMsg(  
     Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData));  
  if (null != jmsInfo)  
  {  
    if (null != jmsInfo.SelectSingleNode("//Dst"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Dst");  
      destinationQueue = xElement.InnerText.ToUpper(  
                         System.Globalization.CultureInfo.CurrentCulture);  
    }  
    if (null != jmsInfo.SelectSingleNode("//Rto"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Rto");  
      replyToQueue = xElement.InnerText.ToUpper(  
                     System.Globalization.CultureInfo.CurrentCulture);  
    }  
  }  
}  
```  
  
 In addition, the code can access all of the MQMD context properties of the message.