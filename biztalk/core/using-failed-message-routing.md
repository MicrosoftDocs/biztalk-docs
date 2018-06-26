---
title: "Using Failed Message Routing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.ops.tsroutingfailure"
ms.assetid: d081934c-600e-44ce-8ba4-fb646d494589
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Failed Message Routing
The error-handling facility allows the designer to designate automated handling of messaging failures as an alternative to the traditional (now default) behavior of placing failed messages in the Suspended queue. This automated handling routes an error message to any subscribing routing destination, such as a send port or orchestration. The error message is a clone of the original message with all previously promoted properties now demoted and with selected properties related to the specific messaging failure promoted to the message context.  
  
> [!WARNING]
>  Failed messages contain a copy of the original message. If the original message contains sensitive information, design your manual and automatic failed message processes so that they avoid accidental disclosure.  
  
## What Does Failed Message Routing Consist Of?  
 When failed message routing is enabled, BizTalk Server does not suspend the message—it routes the message instead. Failed message routing can be enabled on both receive and send ports, with the following results:  
  
- If failed message routing is enabled on a receive port and a message fails in the receive pipeline or in routing, a failed message is generated. In the case where an error occurs in or before the disassembly phase, the error message is a clone of the original interchange.  
  
- If failed message routing is enabled on a send port and the message fails in the send pipeline, a failed message is generated.  
  
  When a failed message is generated, BizTalk Server promotes error-report-related message context properties and demotes regular message context properties before publishing the failed message. Compare this to the default behavior when failed message routing is not enabled: Messages that fail are suspended.  
  
## What Kinds of Messaging Failures Trigger an Error Message?  
 Any failure that occurs in adapter processing, pipeline processing, mapping, or message routing results in an error message if routing for failed messages is enabled. When a messaging error occurs while an orchestration is receiving from a receive port or sending to a send port, the resulting error message is associated with the messaging ports to which the orchestration is bound.  
  
## Subscribing to an Error Message  
 Error messages are delivered to orchestrations or send ports that have subscribed to receive them. A subscription typically selects an error message based on the name of the port in which the messaging error occurred (either a send or a receive port). A subscription might also filter on other properties promoted to the error's message context (for example, **InboundTransportLocation** or **FailureCode**).  
  
## Error Message Specification  
 An error message is a clone of the original failed message, with all previously promoted properties demoted and with a set of error-specific properties promoted to the message context. Previously promoted properties are demoted to avoid unintended delivery to subscribers not designated to receive the error message. The error message is published for distribution to subscribers (orchestrations, send ports, and send port groups).  
  
 The properties that are promoted to the context of an error message all fall under the **ErrorReport** namespace in BizTalk Server. They are as follows:  
  
|Property name|Data type|Promoted|Description|  
|-------------------|---------------|--------------|-----------------|  
|FailureCode|System.String|Yes|Error code. A hexadecimal value that is reported in the BizTalk Server Administration console.|  
|FailureCategory|System.Int32|Yes|This property is not used. Its value is undefined.|  
|Description|System.String|No|Error description. Same diagnostic text as is written to the Application Event Log regarding this messaging failure.|  
|MessageType|System.String|Yes|Message type of failed message, or empty if message type is indeterminate.<br /><br /> BizTalk Server uses the message type to associate messages with their XML schemas. Message type is formed by concatenating the schema namespace with the schema root node: http://mynamespace#rootnode. **Note:**  Messages that fail before their message type is determined do not have this property set.|  
|ReceivePortName|System.String|**Promoted** if the failure happened during inbound processing (in a receive port)<br /><br /> **Not promoted** if the failure happened in a send port.|Name of the receive port where the failure happened.|  
|InboundTransportLocation|System.String|**Promoted** if the failure happened during inbound processing (in a receive port)<br /><br /> **Not promoted** if the failure happened in a send port.|URI of the receive location where the failure happened.|  
|SendPortName|System.String|**Promoted** if the failure happened during outbound processing (in a send port)<br /><br /> **Not promoted** if the failure happened in a receive port.|Name of the send port where the failure happened.|  
|OutboundTransportLocation|System.String|**Promoted** if the failure happened during outbound processing (in a send port)<br /><br /> **Not promoted** if the failure happened in a receive port.|URI of the send location where the failure happened.|  
|ErrorType|System.String|Yes|Indicates the type of message that the error contains. This property always contains the value **FailedMessage**, meaning that the error contains the original failed message.|  
|RoutingFailureReportID|System.String|Yes|This property provides the ID of the routing failure report that BizTalk Server generates when there is a routing failure. A routing failure report is a special message that BizTalk Server generates and suspends. This message does not have a body, but it has the context of the failed message. Using this ID, an error-handling orchestration or a send port can query the MessageBox database and process the routing failure report. For example, an orchestration may want to terminate the routing failure report after it gets the failed message.|  
  
## Handling Error Messages  
 Error handling is specified by an orchestration or send-port subscription whose filter matches the properties that have been promoted to the message context of the error message.  
  
## Security Implications  
 The identity associated with the original message—either its initial identity or its final identity determined by the Resolve Party stage of the receive pipeline—is assigned to the error message.  
  
 The security mechanisms that restrict delivery of messages to authorized subscribing ports and orchestrations also apply to error messages.  
  
 A send port that subscribes to an error message, but is not configured with an appropriate decryption certificate, does not receive error messages that result from messaging failures at or before the decrypt stage of the receive pipeline through which the original message entered BizTalk Server. Instead, the failed messages are placed in the Suspended queue.  
  
## Adapter Messaging Failure  
 If an adapter suspends a message, an error message is published. No error message is generated if the message is not suspended.  
  
## Transactional Receive Pipelines  
 If a transactional receive pipeline throws an exception (specifies that the transaction should be aborted), then the transaction is aborted and an error message is published.  
  
 If a transactional receive pipeline explicitly suspends a message (specifies that MessageDestination = SuspendQueue), then the current transaction is allowed to proceed (and may be committed unless subsequent stages specify to abort it) and the resulting error message is published.  
  
## Solicit-Response Send Ports  
 When a request message is sent from an orchestration and it fails transmission or its response fails inbound processing, the orchestration gets an exception, regardless of whether the failed message has been routed.  
  
 In the case where a solicit-response send port is connected to a request-response receive port, the receive port gets either a response message (if the transmission succeeds) or a NACK (if the transmission fails), regardless of whether the failed message has been routed.  
  
## One-Way Send Ports  
 When a message is sent from an orchestration through a send port configured for delivery notification, then the orchestration receives a delivery notification regardless of whether the error message has been routed. In other words, the send port generates a delivery notification for the orchestration even if the port encounters a messaging failure during processing. The notification confirms delivery to the port, but does not address successful processing through the port.  
  
## Resuming Suspended Messages  
 Most messages that fail inbound processing (that is, processing from and including the receive adapter and up to but not including publication to the message box), and whose failures are not handled, are suspended as resumable. The exception is that request messages from two-way receive ports are suspended as nonresumable.  
  
 Messages are typically suspended in their original form (as they were before pipeline processing), with two exceptions:  
  
-   **Messages suspended by pipeline components.** BizTalk Server suspends this type of message in the same form as it was provided to the failing pipeline component. When the message is resumed, it undergoes pipeline processing from the beginning of the same pipeline. This implies that a pipeline component in a pipeline stage that precedes the stage where the original failure occurred must be prepared to handle the "same" message in a form that is different from the original form in which it processed that message.  
  
-   **Messages from recoverable interchange disassembly that subsequently fail routing.** BizTalk Server suspends this type of message in the same form as it was published. This is the form the message had **after** pipeline execution. When the message is resumed, it skips pipeline processing and is published directly to the MessageBox database.  
  
## Scenarios Leading to Suspended (Non-Resumable) Messages  
 While it is more common for messages to be suspended as resumable, there are some scenarios that lead to non-resumable messages:  
  
-   In an Ordered Delivery send port with continue on failure enabled, if there is a failure in the pipeline, mapping or transmission.  
  
-   In an Ordered Delivery receive port, if the adapter is configured to suspend messages on non-resumable on failure. For example, if the MSMQ adapter setting "On Failure" is set to "Suspend (non-resumable)" or the MQSeries adapter has "Suspend as Non Resumable" enabled, failed messages will be suspended as non-resumable.  
  
-   In a two-way receive port, if the response message fails in the pipeline, mapping, or transmission.  
  
-   In a two-way receive port, if the receive message fails in the pipeline, mapping or transmission. Individual adapter behavior may be different. For example, the HTTP adapter does not suspend messages by default but can be configured to do so.  
  
## See Also  
 [Error Handling](../core/error-handling.md)   
 [Using Acknowledgments](../core/using-acknowledgments.md)   
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)