---
title: "How to Configure a Client Channel Definition File2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a077000a-c7f7-4759-9da6-0507ee211859
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure a Client Channel Definition File
To specify a channel definition, you must provide a client channel definition file for WebSphere MQ Client components to use if the following are true:  
  
-   When configuring send and receive ports, you did not specify a **Channel Name** property.  
  
-   When configuring send and receive ports, you set the **Transaction Supported** property to Yes, and you configured Secure Sockets Layer (SSL) for client/server communication for WebSphere MQ.  
  
### To configure a client channel definition file  
  
1. On your WebSphere MQ Server computer, create the client channel definition file.  
  
    For information about how to create a client channel definition file, refer to IBM WebSphere MQ product documentation.  
  
    After the file is defined, a binary format .TAB file is created. By default, this file is named AMQCLCHL.TAB, and it is typically located in the \<*WebSphere MQ Server installation folder*>\qmgrs\\<QueueManagerName\>\\@ipcc folder.  
  
2. Move the AMQCLCHL.TAB file to the WebSphere MQ client computer on which BizTalk Server is installed, and define the MQCHLLIB and MQCHLTAB environment variables on this computer.  
  
   -   For MQCHLLIB, specify the folder that contains the AMQCLCHL.TAB file. By default, it is the WebSphere MQ client installation folder.  
  
   -   For MQCHLTAB, specify the name of the .TAB file (by default AMQCLCHL.TAB).  
  
   When you are setting up SSL using a client channel definition file, the key repository environment variable (MQSSLKEYR) must also be set on the WebSphere MQ client computer on which BizTalk Server is installed. For MQSSLKEYR, specify the path of the key repository for the client.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)