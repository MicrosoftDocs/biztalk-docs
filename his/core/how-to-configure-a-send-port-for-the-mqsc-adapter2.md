---
description: "Learn more about: How to Configure a Send Port for the MQSC Adapter"
title: "How to Configure a Send Port for the MQSC Adapter2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure a Send Port for the MQSC Adapter
You configure a send port for the BizTalk Adapter for WebSphere MQ by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a send port  
  
1.  In **Start**, select **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
4.  In the **Send Port Properties** window, select **mqsc** in the **Transport Type** list.  
  
5.  Click **Configure**.  
  
6.  In the adapter’s **Transport Properties** window, configure the send port properties (refer to the tables at the end of this procedure).  
  
    > [!NOTE]
    >  The following properties are required to configure a send port:  
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
  
     If you do not specify a **Channel Name** property, you must provide a client channel definition file to enable the WebSphere MQ Client installed on the BizTalk Server computer to communicate with remote queue managers. You must also provide a client channel definition file if you configure Secure Sockets Layer (SSL) to work with transactional messaging. For more information, see [How to Configure a Client Channel Definition File](../core/how-to-configure-a-client-channel-definition-file2.md).  
  
7.  When you have finished configuring the properties, click **OK**.  
  
8.  In the **Send Port Properties** window, in the **Send handler** list, select the host instance on which the send adapter is running.  
  
9. In the **Send pipeline** list, select the pipeline that processes the messages sent through this port.  
  
10. Click **OK**.  
  
11. In the **Send Ports** window, right-click the send port in the **Name** column and select **Enlist**.  
  
12. Right-click the send port in the **Name** column and select **Start**.  
  
     In the **Advanced** section of the **Transport Properties** window, you can set the following send port properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**SSO Affiliate**|Sets the Single Sign-On (SSO) affiliate application. The user ID and password from SSO are used for the MQMD_UserIdentifier, and the MQIIH_Authenticator (or MQCIH_Authenticator) property respectively. This assumes that a valid SSO ticket exists.<br /><br /> Default: Blank|  
    |**Transaction Supported**|When this property is set to **Yes**, the MQSC adapter works in conjunction with the WebSphere MQ Extended Transactional Client (Extended-Client) on the BizTalk Server computer to prevent loss of messages and to guarantee once-and-only-once delivery of messages.<br /><br /> When it is set to **No**, duplication of messages may occur. In this case, the adapter uses the non-transactional WebSphere MQ Client (Base-Client) for integration with MQSeries.<br /><br /> Default: No|  
  
     In the **Channel Definition** section of the **Transport Properties** window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Channel Name**|Name of the channel defined on the MQSeries Server computer that the client communicates with. This must be a ‘Server Connection’ Channel type.<br /><br /> Note that this is a case-sensitive property.|  
    |**Connection Name**|Name of the MQSeries Server that contains the Queue Manager and Queues that the MQSC Adapter sends messages to.<br /><br /> For the TCP transport type, the format to be specified is SERVERNAME(PORT). The port number is equivalent to the port number defined in the Listener associated with the Queue Manager.<br /><br /> The server name can also be specified as an IP address.<br /><br /> For LU6.2, specify the LU Name or LU Pool Name configured in Host Integration Server.|  
    |**Heart Beat**|Number of seconds between checks to verify that the client/server connection is working.<br /><br /> Default: 300|  
    |**Password**|Password that can be used by the MCA when attempting to initiate a secure LU 6.2 session with a remote MCA.<br /><br /> The initial value of this optional property is null.|  
    |**SSL Cipher Specification**|Defines a single CipherSpec for an SSL connection that will be used by the end-point configured in the adapter. Both ends of a WebSphere MQ SSL channel definition must include the attribute, and the value specified here should match the name specified on the server end of the channel. The value is a string with a maximum length of 32 characters.<br /><br /> Required only when SSL is configured for communication between the MQSeries Client and remote Queue Managers.|  
    |**SSL Peer Name**|Used to check the distinguished name (also known as DN) of the certificate from the peer queue manager or client at the other end of a WebSphere MQ channel. If the distinguished name that is received from the peer does not match this value, the channel does not start.<br /><br /> Required only when SSL is configured for communication between the MQSeries Client and Queue Managers.|  
    |**Transport Type**|TCP and LU6.2 are supported.<br /><br /> Default: TCP|  
    |**User Id**|MCA user identifier that is used by MQSeries MCA for authorization to access MQSeries resources.<br /><br /> The initial value is null. This is an optional property. When this attribute is blank, the MCA uses its default user identifier.|  
  
     In the **MQSeries** section of the **Transport Properties** window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Segmentation Allowed**|Set to **Yes** to tell MQSeries Queue Manager to create segmented messages when submitting large messages to MQSeries Queues.<br /><br /> Default: **No**|  
  
     In the **Queue Definition** section of the Transport Properties window, you can set the following properties.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Queue**|MQSeries queue to which the adapter will send messages.<br /><br /> Remote Queue Definitions, Local Queues, Alias Queues, and Transmission Queues are supported.<br /><br /> Note that this is a case-sensitive property.|  
    |**Queue Manager**|Name of MQSeries Queue Manager that contains the queues to which the adapter will send messages.<br /><br /> Clustered Queue Managers are supported.<br /><br /> Note that this is a case-sensitive property.|  
  
13. Click **OK**.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)   
 [How to Configure a Client Channel Definition File](../core/how-to-configure-a-client-channel-definition-file2.md)   
 [How to Configure a Receive Port and a Receive Location for the MQSC Adapter](../core/how-to-configure-a-receive-port-and-a-receive-location-for-the-mqsc-adapter2.md)
