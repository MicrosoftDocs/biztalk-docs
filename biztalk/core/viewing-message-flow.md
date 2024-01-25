---
description: "Learn more about: Viewing Message Flow"
title: "Viewing Message Flow"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Viewing Message Flow
A message flow is the set of contiguous processing steps taken by a message. You access the message view through the shortcut menu that appears when you right-click a service or message instance in the Group Overview page in the BizTalk Server Administration Console. Once in the Message Flow view, you can switch back and forth between the Message Flow view and the Orchestration Debugger.  
  
 The Message Flow view shows you what messages a service instance (pipeline/port or orchestration) sent and received, and details such as the URL, port, and party used. You can also see which preceding service instances handled the messages coming into the service instance you are currently viewing. You can navigate back to these instances and see the messages coming into and going out of these instances. You can also see the subsequent service instances that received messages from the service instance you are currently viewing, and navigate forward to these instances to see the messages coming into and going out of these instances. In other words, you can trace the entire path of an activation message through your business process.  
  
 You can also navigate from an incomplete service instance that is, one that is still processing a message and has not completed, in the Message Flow view to the service instance details for this instance in the BizTalk Server Administration Console to see its current state, such as running, suspended, etc.  
  
 The top of the Message Flow window displays the Service Instance information, such as start and end time, error codes, and version. The bottom of the window displays the Message Activity for the Service Instance, detailing which messages were received or sent. You can view more details for each message instance by selecting the Expand or Collapse buttons. The message instances show all the details by default.  
  
 Next to the In/Out column, target namespace and root element identify the schema. Then you can find the details about the message. Underneath the schema information, appears a link with an item name, for example, EquityLoanReceivePipeline. Clicking the link provides you with the information for that item, thus enabling you to follow the message through it.  
  
 To return to the service that you started with, click the corresponding source or destination item in the other item.  
  
 The following table shows the information displayed for each service.  
  
|Name|Contents|  
|----------|--------------|  
|Instance ID|The Globally Unique Identifier (GUID) associated with the instance.|  
|Host|Name of the Host executing the orchestration or pipeline.|  
|State|Current state of the instance. Possible states are Running, Completed, Manually Suspended, Error, Terminated, In Debug Mode, and Breaking.|  
|Start Time|Time the orchestration/pipeline started.|  
|End Time|Time the orchestration/pipeline completed.|  
|Duration|How long, in milliseconds, the item took to run.|  
|Exit Code|Technical Exit code.|  
|Error Info|Text message about error.|  
|Name|Name of the orchestration or pipeline.|  
|Type|Type of the item—orchestration or pipeline.|  
|Version ID|Unique version of the item.|  
|Deployment Time|When the orchestration/pipeline deployed.|  
  
 Below the Item detail table shows the message activity for the service instances sent or received by the particular orchestration or pipeline. Each row of the table represents one message and you can expand a message instance to show details about the message, such as ID, size, and name of port.  
  
 The following table shows the information that is displayed for each message instance.  
  
|Name|Contents|  
|----------|--------------|  
|In/Out|A Message Received or a Message Sent icon indicates the states of messages.|  
|Message Instance|Target namespace and top-level element; Unparsed Interchange if unknown.|  
|Message Status|Possible statuses: OK, In Transmission, Transmission Failure, Transmission Failure (to be retried), and Transmission Failure (to be resubmitted in backup transport).|  
|Timestamp|Time this particular message was involved in the current action (send/receive).|  
  
 After you expand the message instance, the following information is displayed.  
  
|Name|Contents|  
|----------|--------------|  
|Message Instance ID|GUID of the message.|  
|Size|Size of the message. No value is displayed if the message has no size.|  
|Parts|Number of parts in the message not including shortcut.|  
|Adapter|Adapter used to transmit the message. Some possible adapters are File, HTTP, SOAP, BizTalk Message Queuing, SOAP, or a WCF adapter.|  
|URL|Source or destination URL.|  
|Port|Name of the port the message was sent or received.|  
|Party Name|Name of the party sending/receiving the message. This field displays only if the information is known.|  
|Decryption Certificate|Thumbprint of the certificate used for decrypting the message. This field only displays if a message includes a decryption certificate.|  
|Signature|Signature in the message. This field only displays if the message was signed.|  
|Status Icon|The current status of the message which can include Received, Sent, or in Work Queue).|  
|Source/Target Item URL|The item (Orchestration or Pipeline) identified as the source/destination for the message. When clicked, the system redirects the user to a view for that item instance.|  
  
 When you view an orchestration instance, you can switch to the Orchestration Debugger view by clicking **Switch to Orchestration Debugger**.  
  
## See Also  
 [Working with the Orchestration Debugger View](../core/working-with-the-orchestration-debugger-view.md)   
 [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)
