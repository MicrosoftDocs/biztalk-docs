---
title: "Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive ports, setting transport properties"
  - "transport properties, setting for receive port"
  - "setting transport properties, receive port"
ms.assetid: bccddf84-d92e-469f-aa6f-4234c91a0be9
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port
For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.  
  
### To specify TIBCO EMS transport properties  
  
1.  Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.  
  
2.  Expand **Message Handling** and enter all required information.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |**Message Selector**|Messages are received only if this string evaluates to True with the message in the destination.<br /><br /> Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.<br /><br /> The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax. The syntax is fully described in the TIBCO EMS users guide.<br /><br /> For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.|  
    |**Retry Count**|The retry count for the transport. Default value is 0.|  
    |**Retry Interval**|The period of time the adapter waits before initiating a retry. Default value is five minutes.|  
  
3.  Expand the **Server Connection Definition** and enter all required information.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |**Destination**|Mandatory setting. Defines the name and type of the destination. Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].|  
    |**Port Number**|Port on which the TIBCO EMS server listens.|  
    |**Server Name**|Mandatory setting. Name of the system hosting the TIBCO EMS server.|  
  
4.  Provide credentials using Single Sign-On (SSO).  
  
     There are two methods that you can use to access the TIBCO EMS system. You can use Credentials (user name and password parameters) or Single Sign-On.  
  
    -   Select **Yes** in **Use SSO** to use Single Sign-On.  
  
    -   Select an affiliate application in the list.  
  
         An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS. Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user. These credentials are retrieved from the SSO database for the server system for a specified affiliate application.  
  
         For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).  
  
5.  Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.  
  
    |Parameter|Description|  
    |---------------|-----------------|  
    |`Password`|The user’s password that is used to communicate with a TIBCO EMS daemon.<br /><br /> If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.|  
    |`User Name`|Name of a user that is used to communicate with a TIBCO EMS daemon.<br /><br /> If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.|  
  
6.  Click **Apply**, and then click **OK**.  
  
## See Also  
 [Creating Send Ports](../core/creating-send-ports1.md)   
 [Creating TIBCO Enterprise Message Service Receive Handlers](../core/creating-tibco-enterprise-message-service-receive-handlers.md)