---
description: "Learn more about: BizTalk Adapter for WebSphere MQ"
title: "BizTalk Adapter for WebSphere MQ2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16678e3d-eb24-4f1d-aa95-f786f4ef93be
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# BizTalk Adapter for WebSphere MQ
The Client-Based BizTalk Adapter for WebSphere MQ (MQSC Adapter) is a connectivity solution that enables you to use BizTalk Server in an enterprise with WebSphere MQ as the chosen messaging standard.  
  
 Previously, once-and-only-once delivery of messages between BizTalk Server and WebSphere MQ applications was provided by the Server-Based BizTalk Adapter for WebSphere MQ, which requires MQSeries Server on Windows as an intermediate server between BizTalk Server and non-Windows Queue Managers. To enable once-and-only-once delivery of messages, BizTalk Server and the adapter require WebSphere MQ to participate in a distributed transaction using MSDTC (Microsoft Distributed Transaction Coordinator). MSDTC support has been available only with the Server version of WebSphere MQ on Windows.  
  
 With BizTalk Server, transactional messaging (once-and-only-once delivery) is also available through the MQSC Adapter. This is made possible by the MQSC Adapter working together with the WebSphere MQ Extended Transactional Client (MQ Extended-Client). Like the MQSeries Server, the MQ Extended Client supports distributed transactions using Microsoft Distributed Transaction Coordinator (MSDTC) on Windows. Therefore, the adapter can guarantee once-and-only-once delivery of messages by ensuring that both BizTalk Server and MQ Extended-Client participate in a distributed transaction.  
  
 When receiving messages from MQSeries and submitting them to BizTalk Server, the adapter starts an MSDTC transaction and performs an MQGet with SYNCPOINT so that MQSeries participates in the transaction. The adapter passes this same transaction context to BizTalk Server so that BizTalk Server participates in the same transaction when the adapter submits the message to it. After the message has been submitted, the adapter commits the transaction. When sending messages from BizTalk Server to MQSeries, the adapter starts the transaction and performs an MQPut operation with the SYNCPOINT option. BizTalk Server uses this same transaction to remove the message from the BizTalk Server MessageBox database, after which the adapter commits the transaction.  
  
 You can also configure the MQSC Adapter to support non-transactional messaging when integrating with MQSeries Queues. For this, the MQSC Adapter uses the WebSphere MQ Base-Client. In this case, the adapter only guarantees that no messages are lost. Duplication of messages can occur under failure conditions. Therefore, you should use this configuration option only if the application that is consuming the message from BizTalk Server or MQSeries Queues can handle duplication of messages. To prevent loss of messages, the MQSC adapter first does an MQGET with a browse lock by setting the MQGMO_BROWSE_FIRST and MQGMO_LOCK options. The adapter then submits the message to BizTalk Server. If the submitted message to BizTalk Server is successful, the adapter does a destructive MQGet with MQGMO_MSG_UNDER_CURSOR option. If a failure occurs while submitting the message to BizTalk Server, the adapter does an MQGet with MQGMO_UNLOCK so that additional operations can be performed on the message.  
  
 Both the Server-Based BizTalk Adapter for WebSphere MQ and the Client-Based BizTalk Adapter for WebSphere MQ offer their own advantages. The Client-Based Adapter was not designed to replace the Server-Based Adapter. Instead, it provides an additional option for integration between BizTalk Server and WebSphere MQ.  
  
 The following table compares the client-based MQSC adapter with the server-based MQSeries adapter.  
  
|Feature|Server-Based BizTalk Adapter for WebSphere MQ (MQSeries)|Non-Transactional Client-Based BizTalk Adapter for WebSphere MQ (MQSC)|Transactional Client-Based BizTalk Adapter for WebSphere MQ (MQSC)|  
|-------------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|WebSphere MQ Dependency|Requires WebSphere MQ Server on Windows to communicate with WebSphere MQ Queue Managers on non-Windows Systems. This can be on BizTalk Server or on a remote server running Windows.|Requires WebSphere MQ Client to be installed on BizTalk Server to communicate directly to WebSphere MQ Queue Managers on remote systems.|Requires WebSphere MQ Extended Transactional Client to be installed on BizTalk Server to communicate directly to WebSphere MQ Queue Managers on remote systems.|  
|Receive capability|Yes|Yes|Yes|  
|Static send ports|Yes|Yes|Yes|  
|Dynamic send ports|Yes|Yes|Yes|  
|Polling queues on receive|Yes, with static MQGMO Wait Interval for three seconds.|Yes, with configurable MQGMO Wait Interval.|Yes, with configurable MQGMO Wait Interval.|  
|Supports transactional or non-transactional scenarios|Only transactional scenarios are supported.  Non-transactional configuration is available for test/debug mode, but not supported in production.|Non-transactional only.|Transactional only.|  
|Guarantees once-and-only-once delivery of messages|Yes|No, in failure conditions, duplicate messages can occur either in BizTalk Server or in MQSeries queues. Application is responsible for handling duplicate messages.|Yes|  
|Prevents loss of messages|Yes|Yes|Yes|  
|Performance and scalability characteristics|Provides highest performance; better suited to handle heavy message loads.|Compared to server-based adapter, performance is low because of overhead built in to prevent loss of messages.|Performance is higher than non-transactional adapter, but lower than server-based adapter.|  
|Receive-side conversion|When performing MQGET, MQGMO CONVERT option is specified when configured.|When performing MQGET, MQGMO CONVERT option is specified when configured.|When performing MQGET, MQGMO CONVERT option is specified when configured.|  
|Send-side conversion|Can be configured to convert to code page of MQSeries Server on Windows.|Not applicable|Not applicable|  
|Access to MQSeries headers from Orchestrations and Pipeline Components|Yes|Yes|Yes|  
|Segmentation using Queue Manager capabilities|Yes|Yes|Yes|  
|Security between BizTalk Server and MQSeries Server|COM+ application (MQSAgent) on MQSeries Server on Windows uses COM+ roles to allow users who can access it. On the wire, data is encrypted using Packet Privacy. MQSeries Server on Windows to remote MQSeries Server on non-Windows system can be configured to use SSL.|Configure Secure Sockets Layer (SSL) between MQSeries Client and Server|Configure SSL between MQSeries Client and Server|  
|Dynamically receives from queue using solicit-response send port based on certain match options|Yes|No|No|  
|MQSeries Channel configuration on BizTalk Server|No|Yes, uses Server Connection Channel.|Yes, uses Server-Connection Channel.<br /><br /> To use SSL, Client Channel Definition file must be used.|  
  
## In This Section  
 [MQSC Adapter Features](../core/mqsc-adapter-features2.md)  
  
 [How to Add the MQSC Adapter to a BizTalk Server Installation](../core/how-to-add-the-mqsc-adapter-to-a-biztalk-server-installation1.md)  
  
 [How to Configure a Send Port for the MQSC Adapter](../core/how-to-configure-a-send-port-for-the-mqsc-adapter2.md)  
  
 [How to Configure a Receive Port and a Receive Location for the MQSC Adapter](../core/how-to-configure-a-receive-port-and-a-receive-location-for-the-mqsc-adapter2.md)  
  
 [How to Configure a Client Channel Definition File](../core/how-to-configure-a-client-channel-definition-file2.md)  
  
 [How to Configure the MQSC Adapter for Transactional Messaging](../core/how-to-configure-the-mqsc-adapter-for-transactional-messaging2.md)  
  
 [How to Configure SSL for the MQSC Adapter: Transactional](../core/how-to-configure-ssl-for-the-mqsc-adapter-transactional2.md)  
  
 [MQSC Adapter Schema](../core/mqsc-adapter-schema2.md)
