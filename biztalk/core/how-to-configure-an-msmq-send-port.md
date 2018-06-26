---
title: "How to Configure an MSMQ Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, send ports"
  - "send ports, MSMQ adapters"
  - "configuring [MSMQ adapters], send ports"
ms.assetid: 37313d45-8148-4aaf-a3f2-ea05b3b8b448
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an MSMQ Send Port
You can set MSMQ send port adapter variables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. If properties are not set for the send port, the default send handler values set in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console are used.  

> [!IMPORTANT]
>  If a host instance is associated with an MSMQ send port or receive location, verify the MSMQ service is running on that machine. If the service is not running, the MSMQ receive ports will shut down shortly after they are started, and messages sent to the MSMQ send ports will be suspended.  
>   
>  In a clustered scenario, not only does the clustered MSMQ instance need to be running, but the local MSMQ service on each cluster machine should be running, as well.  

## To configure variables for an MSMQ send port  
 Follow these steps to configure variables for an MSMQ send port:  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new send port or double-click an existing send port to modify it. See [How to Create a Send Port](../core/how-to-create-a-send-port2.md) for more information. Configure all of the send port options. On the **General** tab, in the **Transport** section, specify **MSMQ** for the **Type** option.  

2. On the **General** tab, in the **Transport** section, click the **Configure** button next to **Type**.  

3. In the **MSMQ Transport Properties** dialog box, do the following:  


   |            Use this property            |                                                                                                                            To do this                                                                                                                            |  Data type  | Default value |
   |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|---------------|
   |              **Password**               |                                                                                                 Specify the password for a remote queue. Use with **User Name**.                                                                                                 |   String    |     Blank     |
   |              **User Name**              |                                                             Specify the user name for a remote queue. Use with **Password**. You cannot use the local user of the remote computer for the user name.                                                             |   String    |     Blank     |
   |        **Acknowledgement Type**         | Specify the type of acknowledgement message for Message Queuing to return to the sending application. You can select more than one acknowledgment type. Any of the acknowledgement types in the **System.Messaging.AcknowledgeTypes** enumeration are available. |   String    |     None      |
   |        **Administration Queue**         |                                                                                                Specify the queue name that receives the acknowledgement message.                                                                                                 |   String    |     Blank     |
   |              **Body Type**              |                                                                               Specify the message body type in MSMQ. Valid values are members of the .NET **VarEnum** enumeration.                                                                               |     Int     |     8209      |
   |       **Certificate Thumbprint**        |    Specify the thumbprint of the certificate to use for message authentication. Use this property in combination with the **Use Authentication** property to verify the message. Use the **User Name** and **Password** properties to gain access to queues.     |   String    |     Blank     |
   |          **Destination Queue**          |                     Specify the destination queue. For more information about queues, see [Message Queuing Queues](../core/message-queuing-queues.md). **Note:**  The URI for a send port or receive location cannot exceed 256 characters.                      |   String    |     Blank     |
   |        **Encryption Algorithm**         |                                                                                                Select **RC2**, **RC4**, or **None** for the encryption algorithm.                                                                                                |    Enum     |     None      |
   | **Maximum Message Size (in kilobytes)** |                                                                                       Specify the maximum message size for messages that you send to the specified queue.                                                                                        | UnsignedInt |     1024      |
   |          **Message Priority**           |                                                                                                                    Set the message priority.                                                                                                                     |    Enum     |    Normal     |
   |             **Recoverable**             |                                                                                                  Specify whether to guarantee the recoverability of a message.                                                                                                   |   Boolean   |     False     |
   |        **Support Segmentation**         |                                                                                        Set this Boolean property value to **True** to segment messages larger than 4 MB.                                                                                         |   Boolean   |     False     |
   |               **Timeout**               |                                                                    Specify the maximum time to wait for the messages to reach the destination queue. Applies only when you use transactions.                                                                     |     Int     |       0       |
   |            **Timeout Unit**             |                                                                      Set the unit to use for the **Timeout** property.<br /><br /> Select **Days**, **Hours**, **Minutes**, or **Seconds**.                                                                      |    Enum     |     Days      |
   |            **Transactional**            |                                                                                               Set this value to **True** to send messages if you use transactions.                                                                                               |   Boolean   |     False     |
   |         **Use Authentication**          |     Set this Boolean property value to **True** to control authentication. Use this property in combination with the **Certificate Thumbprint** property to verify the message. Use the **User Name** and **Password** properties to gain access to queues.      |   Boolean   |     False     |
   |        **Use Dead Letter Queue**        |                                                                                    Set this value to **True** to send messages to the dead letter queue if a failure occurs.                                                                                     |   Boolean   |     True      |
   |          **Use Journal Queue**          |                                                                                   Set this value to **True** to save a copy of the message whenever the message is processed.                                                                                    |   Boolean   |     False     |


4. Click **OK** and **OK** again to save settings.  

## See Also  
 [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md)   
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)