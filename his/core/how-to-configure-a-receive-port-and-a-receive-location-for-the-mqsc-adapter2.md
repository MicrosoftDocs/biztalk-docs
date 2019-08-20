---
title: "How to Configure a Receive Port and a Receive Location for the MQSC Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16871704-2295-44ef-b414-6bd1e28ed7ce
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Configure a Receive Port and a Receive Location for the MQSC Adapter
You configure a receive port and receive location for the BizTalk Adapter for WebSphere MQ by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a receive port and receive location  
  
1.  In **Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
4.  In the **Receive Port Properties** window, configure properties for the port, and then click **OK**.  
  
5.  In the console tree, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location.**  
  
6.  In the **Select a Receive Port** window, click the receive port that you created in the previous step, and then click **OK**.  
  
7.  In the **Receive Location Properties** window, select the MQSC adapter as the Transport Type, and then click **Configure**.  
  
8.  In the adapter’s **Transport Properties** window, configure the receive location’s properties (refer to the tables at the end of this procedure).  
  
    > [!NOTE]
    >  The following properties are required to configure a receive location:  
    >   
    >  **Channel Name** (This is a case-sensitive property.)  
    >   
    >  **Connection Name**  
    >   
    >  **Transport Type**  
    >   
    >  **Queue** (This is a case-sensitive property.)  
    >   
    >  **Queue Manager** (This is a case-sensitive property.)  
    >   
    >  If you do not specify a **Channel Name** property, you must provide a client channel definition file to enable the WebSphere MQ Client installed on the BizTalk Server computer to communicate with remote queue managers. You must also provide a client channel definition file if you configure Secure Sockets Layer (SSL) to work with transactional messaging. For more information, see [How to Configure a Client Channel Definition File](../core/how-to-configure-a-client-channel-definition-file2.md).  
  
9. When you have finished configuring the properties, click **OK**.  
  
10. In the **Receive Location Properties** window, in the **Receive handler** list, select the instance of the BizTalk Server host on which the receive location will run.  
  
     The receive handler must be running on this host.  
  
11. In the **Receive pipeline** list, select the receive pipeline to use to receive messages at this receive location.  
  
12. Click **OK**.  
  
13. In the **Receive Locations** window, right-click the Receive Location in the **Name** column and select **Enable**.  
  
     **Receive Location Properties**  
  
     In the **Advanced** section of the **Transport Properties** window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Data Offset for Headers**|The adapter uses values from the MQSeries headers (the MQMD, MQXQH, MQIIH, and MQCIH structures) and populates corresponding values in the BizTalk Server context properties. By default, the adapter removes these MQSeries properties from the message body. Set to **No** to retain the properties in the message body.<br /><br /> Default: **Yes**|  
    |**Event Log Error Threshold**|The maximum number of the same error to be logged for certain error conditions. The adapter continues operating and, if the adapter recovers, it logs the event in the Application log.<br /><br /> Default: 10|  
    |**Ordered**|Set to **Yes** to maintain the order of the messages as they are received from the MQSeries queue and submitted to the BizTalk Server MessageBox.<br /><br /> For the send side, the adapter sends the message to the queue in the same order that it receives it from the message box.<br /><br /> Set to **No** to not maintain message order.<br /><br /> For send-side ordering, if you are not using Orchestration, you must enable Ordered Delivery in the Transport Advanced Options of the send port configuration.<br /><br /> For receive-side ordering, if you are using Orchestration, you must also set the **Ordered Delivery** property to **True** in your orchestration for the receive location.<br /><br /> Ordered delivery can decrease performance; unless you require ordered delivery, it is not recommended.<br /><br /> Default: **No**|  
    |**Stop on error**|Set to **Yes** to stop processing if there is an error. This option ends the transaction and disables the receive location if there is an error.<br /><br /> Default: **No**|  
    |**Suspend As Non Resumable**|Set to **Yes** to move a message to the suspended queue when there is an error and indicate if it is resumable or not.<br /><br /> Enabling this value does not preserve ordered delivery when there is an error, but does allow the receive location to continue receiving messages.<br /><br /> Default: **No**|  
    |**Transaction Supported**|When set to **Yes**, the MQSC adapter works together with the WebSphere MQ Extended Transactional Client (Extended-Client) on the BizTalk Server computer to prevent loss of messages and to guarantee once-and-only-once delivery of messages.<br /><br /> When set to **No**, duplication of messages may occur. In this case, the adapter uses the non-transactional WebSphere MQ Client (Base-Client) for integration with MQSeries.<br /><br /> Default: **No**|  
    |**Wait Interval**|When MQGet is performed to retrieve messages from MQSeries Queue, MQGMO option for Wait Interval can be set. If there are no messages in the queue, the adapter waits for the specified time (in seconds) before closing the client request. As soon as messages arrive on the queue, the adapter starts retrieving the messages.<br /><br /> Default: 3|  
  
     In the **Channel Definition** section of the Transport Properties window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Channel Name**|Name of the channel defined on the MQSeries Server computer that the client communicates with. This must be a ‘Server Connection’ Channel type.<br /><br /> Note that this is a case-sensitive property.|  
    |**Connection Name**|Name of the MQSeries Server that contains the Queue Manager and Queues that the MQSC Adapter receives messages from.<br /><br /> For the TCP transport type, the format to specify is SERVERNAME(PORT). Port number is equivalent to the port number defined in the Listener associated with the Queue Manager.<br /><br /> The server name can also be specified as an IP address.<br /><br /> For LU6.2, specify the LU Name or LU Pool Name configured in Host Integration Server.|  
    |**Heart Beat**|Number of seconds between checks to verify that the client/server connection is working.<br /><br /> Default: 300|  
    |**Password**|Password that can be used by the MCA when trying to initiate a secure LU 6.2 session with a remote MCA.<br /><br /> The initial value of this optional property is null.|  
    |**SSL Cipher Specification**|Defines a single CipherSpec for an SSL connection that will be used by the end-point configured in the adapter. Both ends of a WebSphere MQ SSL channel definition must include the attribute, and the value specified here should match the name that is specified on the server end of the channel. The value is a string with a maximum length of 32 characters.<br /><br /> Required only when SSL is configured for communication between the MQSeries Client and remote Queue Managers.|  
    |**SSL Peer Name**|Used to check the distinguished name (also known as DN) of the certificate from the peer queue manager or client at the other end of a WebSphere MQ channel. If the distinguished name that is received from the peer does not match this value, the channel does not start.<br /><br /> Required only when SSL is configured for communication between the MQSeries Client and Queue Managers.|  
    |**Transport Type**|TCP and LU6.2 are supported.<br /><br /> Default: TCP|  
    |**User Id**|MCA user identifier that is used by MQSeries MCA for authorization to access MQSeries resources.<br /><br /> The initial value is null. This is an optional property. When this attribute is blank, the MCA uses its default user identifier.|  
  
     In the **MQSeries** section of the Transport Properties window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Character Set**|Character set to which the message should be converted when messages are received from the MQSeries Queue. If this property is set to a value other than None, the adapter sets the MQGMO CONVERT option when performing an MQGet.<br /><br /> **None**: Do not convert.<br /><br /> **UCS-2 and UTF-16**: Convert to these character sets. MQSeries does not distinguish between them.<br /><br /> UTF-8: Convert to the UTF-8 character set.<br /><br /> Default: None|  
    |**Segmentation Allowed**|Set MQSeries to assemble segmented messages or to get the message as is. Use No Action to read messages from the MQSeries queue without enabling segmentation. Use Complete Message to have MQSeries assemble segmented messages before passing them on to the adapter.<br /><br /> Default: **No Action**|  
  
     In the **Performance** section of the Transport Properties window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Maximum Batch Size**|Maximum size of a batch of messages in KB.<br /><br /> This property and **Maximum Messages in Batch** work together so that the limit is whichever value the adapter reaches first.<br /><br /> Default: 100|  
    |**Maximum Messages in Batch**|Maximum number of messages from 1 to 10,000 in a batch.<br /><br /> This property and **Maximum Batch Size** work together so that the limit is whichever value the adapter reaches first.<br /><br /> Default: 10|  
    |**Threads**|Number of threads used per receive location.<br /><br /> Default: 2|  
  
     In the **Queue Definition** section of the Transport Properties window, you can set the properties listed in the following table.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Queue**|MQSeries queue from which the adapter will receive (MQGet) messages.<br /><br /> Transmission Queues, Local Queues, Alias Queues are supported.<br /><br /> Note that this is a case-sensitive property.|  
    |**Queue Manager**|Name of MQSeries Queue Manager that contains the Queues from which the adapter will retrieve messages.<br /><br /> Clustered Queue Managers are supported.<br /><br /> Note that this is a case-sensitive property.|  
  
14. Click **OK**.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)   
 [How to Configure a Client Channel Definition File](../core/how-to-configure-a-client-channel-definition-file2.md)   
 [How to Configure a Send Port for the MQSC Adapter](../core/how-to-configure-a-send-port-for-the-mqsc-adapter2.md)