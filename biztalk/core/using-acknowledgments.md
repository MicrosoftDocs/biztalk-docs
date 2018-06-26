---
title: "Using Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, publishing"
  - "messages, acknowledgements"
  - "BTS.AckSendPortID property"
  - "BTS.AckSendPortName property"
  - "BTS.AckType property"
  - "BTS.AckFailureCode property"
  - "BTS.AckID property"
  - "acknowledgements, positive"
  - "SOAP fault"
  - "BTS.AckReceivePortID property"
  - "BTS.AckReceivePortName property"
  - "BTS.AckInboundTransportLocation property"
  - "BTS.AckOutboundTransportLocation property"
  - "messages, successful transmission"
  - "BTS.AckDescription property"
  - "orchestrations, messages"
  - "acknowledgements, negative"
  - "BTS.CorrelationToken property"
  - "BTS.AckFailureCategory property"
  - "positive acknowledgements (ACK)"
  - "BTS.AckOwnerID property"
ms.assetid: 2e5986d4-9633-4b7b-8ff3-fa3da93c5400
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Acknowledgments
The BizTalk Messaging Engine generates positive acknowledgments (ACK) and negative acknowledgments (NACK) in response to conditions encountered during the processing of a message through a port. BizTalk Server publishes a positive acknowledgment to indicate successful transmission of a message and a negative acknowledgment to indicate transmission failure and suspension of a message.  
  
## Why Use Acknowledgments?  
 Positive and negative acknowledgments provide strong feedback that you can use to determine if a message arrived at its destination or encountered one or more problems along the way. For example, acknowledgments are useful when:  
  
- You want to monitor a receive port for a new trading partner for schema validation and other errors.  
  
- You want to mark the status of a loan request sent out for approval as "in process" if it is successfully sent to a partner for approval or "failed" if transmission fails (for example, if the partner's server is down).  
  
- You process interchanges containing multiple purchase orders and want to track the number of orders that are transmitted or fail transmission.  
  
  You can accomplish each of these scenarios by using acknowledgments and content-based routing that uses filters.  
  
## Routing Acknowledgments  
 When an ACK or NACK is published, all of the message context properties from the message that caused the ACK/NACK are demoted. Any properties that were promoted do not flow to the acknowledgment. To route an acknowledgment, build a filter using the following properties from the **BTS** namespace:  
  
|Property name|Data type|Description|  
|-------------------|---------------|-----------------|  
|BTS.AckFailureCategory|xs:int|Identifies the **ErrorCategory**, which gives the place and reason for the suspension.|  
|BTS.AckFailureCode|xs:string|Identifies the **ErrorCode**, which gives the place and reason for the suspension.|  
|BTS.AckType|xs:string|Value is ACK for a positive acknowledgment and NACK for a negative acknowledgment.|  
|BTS.AckID|xs:string|Identifies the **MessageID** of the original message.|  
|BTS.AckOwnerID|xs:string|Identifies the instance ID from the original message.|  
|BTS.CorrelationToken|xs:string|Identifies the correlation token from the original message if one is present.|  
|BTS.AckDescription|xs:string|Identifies the **ErrorDescription**, which gives the place and reason for the suspension.|  
|BTS.AckSendPortID|xs:string|Identifies the **SendPortID** from the original message.|  
|BTS.AckSendPortName|xs:string|Identifies the **SendPortName** from the original message.|  
|BTS.AckOutboundTransportLocation|xs:string|Identifies the **OutboundTransportLocation** from the original message.|  
|BTS.AckReceivePortID|xs:string|Identifies the **ReceivePortID** from the original message.|  
|BTS.AckReceivePortName|xs:string|Identifies the **ReceivePortName** from the original message.|  
|BTS.AckInboundTransportLocation|xs:string|Identifies the **InboundTransportLocation** from the original message.|  
  
> [!NOTE]
>  The properties that contain error information are not present in ACKs because they signal a positive delivery.  
  
## Negative Acknowledgment Message Body  
 Much of the important information about a positive or negative acknowledgment is contained in the context properties. In addition to the context properties, NACKs also contain a message body part containing a SOAP fault. The format of the SOAP fault is as follows:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
  <SOAP:Body>  
    <SOAP:Fault>  
      <faultcode>Microsoft BizTalk Server Negative Acknowledgment </faultcode>  
      <faultstring>An error occurred while processing the message, refer to the details section for more information </faultstring>  
      <faultactor>C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml</faultactor>  
      <detail>  
        <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
          <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
          <ErrorCode>0xc0c01658</ErrorCode>  
          <ErrorCategory>0</ErrorCategory>  
          <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".  </ErrorDescription>  
        </ns0:NACK>  
      </detail>  
    </SOAP:Fault>  
  </SOAP:Body>  
</SOAP:Envelope>  
```  
  
 The exception message raised by the adapter is in the SOAP Detail section in the ErrorDescription element.  
  
### Accessing the Message Body from an Orchestration  
 If you have an orchestration port that requires delivery notification, the DeliveryFailureException that is thrown on a transmission failure is deserialized from the SOAP fault that is contained in the NACK message body. To access the exception message string from within your orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml as shown in the following code:  
  
```  
// Cast the DeliveryFailureException to a SoapException…  
System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
//e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
//object type created in an Exception handler  
```  
  
 The preceding code sample returns an XML fragment similar to the following:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
  <ErrorCode>0xc0c01658</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".</ErrorDescription>  
</ns0:NACK>  
```  
  
## When Is an Acknowledgment Published?  
 Both positive (ACK) and negative (NACK) acknowledgments are published to the MessageBox database at the point of failure provided there is at least one matching subscription. For example, if BizTalk Server cannot find a matching schema for a message read from a receive port and there are no NACK subscriptions, it suspends the message (if failed message routing has not been enabled) and does not publish a NACK  
  
## See Also  
 [Error Handling](../core/error-handling.md)   
 [Using Failed Message Routing](../core/using-failed-message-routing.md)