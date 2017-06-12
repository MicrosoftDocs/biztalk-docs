---
title: "Message Details Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.messagedetails.properties"
ms.assetid: f01fa36d-cf58-4c0f-afba-3b9e1eceea96
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Details Properties Dialog Box
Use the **Message Details Properties** window to view details of messages in the message box. You cannot edit messages or message properties, but you can turn on message tracking and save the message to another location. The maximum message part size that the **Message Details Properties** window can display is one megabyte (MB); the complete message may be larger than 1 MB, but no single part may be. If a message part is too large to be displayed in the message viewer, you must open the message part using a third-party program. The same window is used for message routing failure reports, in which case, the window title will be "Routing failure report for Message \<Message GUID>."  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Message Type**|This property specifies the type of the BizTalk message. The message type is defined as a concatenation of the document schema namespace and the document root node. Either disassembler components or the orchestration sets this property. The message must have this property set in order to be received by a strongly typed port in the orchestration.|  
|**Message ID**|Displays the unique ID of the message.|  
|**Originator Party ID**|Displays the unique ID of the party that sent the message. If no party corresponds to the sender, then the guest security ID **s-1-5-7** is used.|  
|**Originator Security ID**|Displays the security ID of the message sender.|  
|**Part Count**|Displays the number of parts within the message.|  
|**Body Part Name**|Displays the name of the body part.|  
|**Create Time**|Displays the time when the message was created.|  
|**Host**|Displays the name of the host with which this message is associated.|  
|**Adapter**|Displays the type of adapter that was used to receive the message or the type of adapter to use when sending the message.|  
|**URI**|Displays the address from which the message was received (for an inbound message) or where message will be sent (for an outbound message).|  
|**Service Name**|Displays the name of the service, such as an orchestration name or a port name.|  
|**Service Class**|Displays the kind of message selected. Possible values are Messaging, Orchestration, and Routing Failure.|  
|**Service Instance ID**|Displays the Global User Identification (GUID) that identifies the service instance.|  
  
## Context Tab  
 Use this tab to view system-specific and component-specific properties, such as adapters and pipeline components properties, for the selected message. The properties that appear depend primarily on which component processed the message. To view properties for a message, click the link associated with the adapter that processed the message.  
  
### Adapter Properties  
  
#### File Adapter  
 [File Adapter Property Schema and Properties](../core/file-adapter-property-schema-and-properties.md)  
  
#### FTP Adapter  
 [FTP Adapter Property Schema and Properties](../core/ftp-adapter-property-schema-and-properties.md)  
  
#### HTTP Adapter  
 [HTTP Adapter Property Schema and Properties](../core/http-adapter-property-schema-and-properties.md)  
  
#### MQSeries Adapter  
 [MQSeries Context Properties](../core/mqseries-context-properties.md)  
  
#### MSMQ Adapter  
 [MSMQ Adapter Property Schema and Properties](../core/msmq-adapter-property-schema-and-properties.md)  
  
#### POP3 Adapter  
 [POP3 Adapter Property Schema and Properties](../core/pop3-adapter-property-schema-and-properties.md)  
  
#### SMTP Adapter  
 [SMTP Adapter Property Schema and Properties](../core/smtp-adapter-property-schema-and-properties.md)  
  
#### SOAP Adapter  
 [SOAP Adapter Property Schema and Properties](../core/soap-adapter-property-schema-and-properties.md)  
  
#### WSS Adapter  
 [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md)  
  
### System Properties  
 System properties are those used internally by the BizTalk Server messaging engine and its components.  
  
### MIME Components Properties  
 MIME components properties are those used to set message and part context properties for MIME encoding.  
  
### BTF Components Properties  
 BizTalk Framework (BTF) properties are used to set message and part context properties for the BizTalk Framework Disassembler pipeline component.  
  
### XML Normalization Components Properties  
 XML Normalization or "XML Norm" refers to the conversion of messages from custom formats into XML representation. XML Norm properties are set and used by XML and flat file assemblers and disassemblers.  
  
### Error Report properties  
 At each point along the pathway that a message follows through the BizTalk Server messaging subsystem, failures can occur in the BizTalk Server infrastructure and in custom pipeline components, orchestrations, and so forth. If you have specified error reporting for the port through which a message is entering or will leave, BizTalk Server publishes an error report message derived from the failing message. The Error Report message is routed to the subscribing routing destination, such as a send port or orchestration; all previously promoted properties are demoted and selected properties related to the specific messaging failure are promoted to the message context. For more information, see [Using Failed Message Routing](../core/using-failed-message-routing.md).  
  
### Message Tracking Properties  
 The BizTalk Server engine uses Message tracking properties internally to preserve tracking-specific information.  
  
## Message Parts Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the name of the message part.|  
|**Character set**|Displays the encoding of the message; the character set is most often UTF-8.|  
|**Content type**|Displays the format used for the content; most common content types are text/XML, text/plain, and text/HTML.|  
|**Size**|Displays the message size in bytes.|  
|**Part ID**|Displays the unique identifier for the message part.|  
  
## Body Tab  
 You use the **Body** tab to view messages in either text or binary format. Ability to view the message body is controlled by role-based access; if you do not have the required privileges to view the message, you will see a message to that effect. The **Body** tab has two subordinate tabs, which you select on the right-hand side of the window; these are the **Text** tab and the **Binary** tab.  
  
### Text Tab  
 Click the **Text** tab to view the message in ASCII characters, if the message is decodable.  
  
### Binary Tab  
 Click the **Binary** tab to view the message in binary form.  
  
## File Menu  
 Use the **File** menu to track or save messages, or to exit from the **Message Details** window. The **File** menu displays the following options:  
  
-   **Save Message**. Click to display the **Save Message** dialog box.  
  
-   **Track Message**. Click to turn on message tracking for the displayed message. A confirmation window appears that requires you to confirm the tracking request. If the message is no longer in the Message Box (terminated or completed), an error message informs you that the message is no longer available.  
  
-   **Exit**. Click to close the **Message Details Properties** window.  
  
## See Also  
 [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)