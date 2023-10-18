---
title: "Create TIBCO EMS send artifacts"
description: Create the send port, and configure the transport properties to use the TIBCO Enterprise Message Service adapter in BizTalk Server
ms.custom: ""
ms.date: "10/23/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating  TIBCO Enterprise Message Service Send Handlers
This section explains how to set the send port to connect to TIBCO Enterprise Message Service (EMS) and how to include XML in your orchestration to interact with TIBCO EMS at run time.  


## Create a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand your application.  
  
2.  Right-click **Send Ports**, select **New**, and then select **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties**, do the following:  
  
    1.  Type a name for the send port, for example, `SendToTIBCOEMS`.  
  
    2.  From the **Type** drop-down list, select **TIBCO EMS**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the **Send Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**. From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  

        > [!NOTE]
        > The BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit for send, and XMLReceive for receive.  
  
    6.  Select **Configure** to configure the send port.  
  
4.  In the **TIBCO EMS Transport Properties** dialog box, do the following:  
  
    1.  Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.  
  
         You do not have to set the logon information.  
  
    2.  In the list, select the affiliate application you created to represent the TIBCO EMS system.  
  
    3.  For **Use SSO**, select **Yes**.  
  
    4.  Select **OK**.  
  
5.  Select **OK**. 

## Set send port transport properties
The TIBCO Enterprise Message Service transport properties are configured in design time and used in run time. In the **Transport Properties**, you set the connection and credential parameters specific to the server system and the objects you are trying to access.  
  
 ![Screenshot that shows the TIBCO EMS Transport Properties dialog box.](../core/media/tib-tibcoemssendtransportpropertiess.gif "TIB_TIBCOEMSSendTransportPropertiess")  
  
  
1.  In the **Transport Properties**, expand **System Definition**, and enter all required information for connection to the TIBCO EMS server.  
  
     You must set configuration parameters to connect Microsoft BizTalk Adapter for TIBCO Enterprise Message Service to TIBCO EMS. **This data is case sensitive.**  
  
2.  Expand **Message Handling**, and enter all required information.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |`Message Expiration Time`|An integer that describes the length of time the message stays on the queue or topic; after the time expires, the message is deleted by the TIBCO EMS server.<br /><br /> It is synonymous to the EMS.Expiration message property header. It can be overridden with the orchestration.<br /><br /> Default value is 0 milliseconds, which means that the message will not expire from the destination.|  
    |`Message is Persistent`|Messages are written to disk by the TIBCO EMS server before they are acknowledged.<br /><br /> This is the TibcoEMS.DeliveryMode header property. It instructs sent messages to be persisted in the queue by the server before acknowledging reception of the message to the adapter.<br /><br /> Default value is **True**.|  
    |`Message Priority`|Numeric ranking from 0 to 9, which defines the priority of the message; the larger the value, the higher the priority.<br /><br /> Priority affects the order in which the server delivers messages to consumers (higher values first).<br /><br /> The JMS specification defines ten levels of priority value, from zero (lowest priority) to 9 (highest priority). The specification suggests that clients consider 0–4 as gradations of normal priority, and priorities 5–9 as gradations of expedited priority.<br /><br /> Default value is **4**.|  
  
3.  Expand **Server Connection Definition** and enter all required information.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |`Destination`|Mandatory setting. Defines the name and type of the destination. For example: staticqueue[Q1].<br /><br /> Defines the queue or topic with the following format: {static}{dynamic]Queue[queuename] or {static}{dynamic]Topic[topicname]. **Note:**  You can send a message to a destination that does not exist. In such a case, TIBCO Enterprise Message Service creates the destination; this is referred to as a *Dynamic Destination*. This is a destination created by a producer and deleted when the message is consumed and the producer disconnects. A *static destination* is a destination which can only created by a TIBCO Enterprise Message Service Administrator. You cannot connect to a dynamic port when you open a connection to a destination because BizTalk Adapter for TIBCO Enterprise Message Service uses a name lookup mechanism on the server. Only static ports are visible when you are using the name lookup. When connecting to a dynamic port, you can use static destinations; however, if no destination by that name exists, a destination is created. Destination lets you explicitly specify the type of destination to use when defining the port. The syntax for the Destination is not case sensitive: staticqueue[queue_name], statictopic[topic_name], dynamicqueue[queue_name]; dynamictopic[topic_name].|  
    |`Port Number`|Port on which the TIBCO EMS server listens.|  
    |`Server Name`|Mandatory setting. Name of the system hosting the TIBCO EMS server.|  
  
4.  Provide credentials using Single Sign-On (SSO).  
  
     You can use two methods to access the TIBCO EMS system. You can use Credentials (User Name and Password parameters) or Single Sign-On.  
  
    -   Select **Yes** in the **Use SSO** to use Single Sign-On.  
  
    -   Select an affiliate application from the list.  
  
         An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS. BizTalk Adapter for TIBCO EMS uses the credentials of an application user. These credentials are retrieved from the SSO database for the server system for a specified affiliate application.  
  
         For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).  
  
5.  In **Transaction Support**, select **Yes** if this send port will support transactions.  
  
     If you enable transaction support on the port, all orchestrations using this port must be transactional; otherwise, all calls are rolled back (for example, are not committed). The scope object added to the orchestration controls the transaction life-cycle.  
  
6.  Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |`Password`|The user’s Password used to communicate with a TIBCO EMS daemon.<br /><br /> If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.|  
    |`User Name`|Name of a user used to communicate with a TIBCO EMS daemon.<br /><br /> If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.|  
  
7.  Click **Apply**, and then click **OK**.  

   
## Next steps
[Create receive artifacts](../core/creating-tibco-enterprise-message-service-receive-handlers.md)  
[TIBCO EMS message context properties](../core/message-context-properties-in-biztalk-server.md)