---
description: "Learn more about: How to Configure an MSMQ Receive Location"
title: "How to Configure an MSMQ Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSMQ adapters, receive locations"
  - "receive locations, MSMQ adapters"
  - "configuring [MSMQ adapters], receive locations"
ms.assetid: ba25cf43-18f1-4c19-84fb-74c7b82b95a9
caps.latest.revision: 43
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an MSMQ Receive Location
You can set MSMQ receive location adapter variables in the BizTalk Server Administration console. If properties are not set in the receive location, the default receive handler values set in the BizTalk Server Administration console are used.  
  
> [!NOTE]
>  Before completing the following procedure you must have already added a receive port. For more information see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
> [!IMPORTANT]
>  If a host instance is associated with an MSMQ send port or receive location, verify the MSMQ service is running on that machine. If the service is not running, the MSMQ receive ports will shut down shortly after they are started, and messages sent to the MSMQ send ports will be suspended.  
>   
>  In a clustered scenario, not only does the clustered MSMQ instance need to be running, but the local MSMQ service on each cluster machine should be running, as well.  
  
## To configure variables for an MSMQ receive location  
 Follow these steps to configure variables for an MSMQ receive location:  
  
1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.  
  
2.  In the BizTalk Server Administration console, in the left pane, click the **Receive Port** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  
  
3.  In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.  
  
4.  In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **MSMQ** from the drop-down list, and then click **Configure**.  
  
5.  In the **MSMQ Transport Properties** dialog box, do the following:  
  
    |Use this|To do this|Date type|Default value|  
    |--------------|----------------|---------------|-------------------|  
    |**Password**|Set a password to use for a remote queue.|String|Blank|  
    |**User Name**|Determine the user name to use, in combination with the password, for access to a remote queue. You cannot use the local user of the remote computer for the user name.|String|Blank|  
    |**Batch Size**|Configure the batch size. The MSMQ adapter submits messages to the MessageBox database in batches. The default batch size is 20, and the minimum batch size is 1. **Note:**  If the **Transactional** property for the receive location is set to **True**; each message batch is submitted to the MessageBox database under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction. The MSDTC transaction that is created for a message batch remains open until every message in the batch has been persisted to the MessageBox and placed in the appropriate subscriber queue. Therefore the duration of this MSDTC transaction is increased as the **Batch Size** parameter is increased. Since having a large number of MSDTC transactions open simultaneously can negatively impact overall performance, the **Batch Size** parameter should not be set to a very large value when transaction support is enabled.|Int|20|  
    |**On Failure**|Specify how the adapter should respond to an error. Set this property to one of the following values:<br /><br /> -   **Stop.** Stop receiving messages through this receive location if an error condition occurs.<br />-   **Suspend(non-resumable).** Suspend messages and mark as non-resumable.<br />-   **Suspend(resumable).** Suspend messages and mark as resumable. **Important:**  If the **True** option for **Ordered Processing** property, the **Stop** option for the **On Failure** property, and the **False** option for the **Transactional** property are applied at the same time, then any messages that fail delivery will not be suspended or left in the source queue. In this scenario, message loss can occur. To prevent data loss, when using the **Ordered Processing** feature, the **Stop** option for the **On Failure** property should only be applied if the **True** option for the **Transactional** property is applied. Then, if a message delivery failure occurs, the original message will be left in the source MSMQ queue. If the **Ordered Processing** property is set to a value of **False** then the **On Failure** property will not take effect and if a message delivery failure occurs the message will be suspended with a status of **Suspended (resumable)**.|String|Suspend(resumable)|  
    |**Ordered Processing**|Set this property to **True** or **False**. This indicates whether to process messages serially. Setting the property to **True** will accommodate ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the **Ordered Delivery** option set to **True**. For more information see [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md).<br /><br /> Setting this property to **True** also optimizes resource usage when handling large messages by making the adapter single-threaded. For more information, see [Sending and Receiving Large Messages Using the MSMQ Adapter](../core/sending-and-receiving-large-messages-using-the-msmq-adapter.md).|Boolean|False|  
    |**Queue**|Type a valid queue path. Depending on the queue path you specify, the system performs the appropriate validations. **Note:**  The URI for a send port or receive location cannot exceed 256 characters. **Note:**  MSMQ Receive adapter uses a polling mechanism to monitor the specified MSMQ queue for new messages every 0.5 seconds. This 0.5 second interval is a fixed interval.|String|Blank|  
    |**Transactional**|Set this property to **True** or **False**. **Note:**  The adapter supports transactional reads of remote queues with Message Queuing 4.0 or later only. In this scenario both the BizTalk Server and the remote Message Queuing server must be running Message Queuing 4.0 or later. <br /><br /> For more information, see [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md) and [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).|Boolean|False|  
  
    > [!NOTE]
    >  The **User Name** and **Password** apply only to Windows accounts used to access remote queues.  
  
6.  Click **OK**.  
  
7.  In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location, and click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
## See Also  
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)
