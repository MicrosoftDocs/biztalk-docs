---
title: "Walkthrough: Creating a BizTalk Application That Uses the MQSeries Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IBM WebSphere MQ queues"
  - "MQSeries adapters, tutorial"
  - "MQSeries adapters, testing"
  - "tutorials, MQSeries adapters"
  - "MQSeries adapters, IBM WebSphere MQ queues"
  - "testing, MQSeries adapters"
  - "MQSeries adapters, queues"
  - "configuring [MQSeries adapters], tutorial"
ms.assetid: e9e169e4-d41c-4e5d-b165-7bd36b481f24
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Creating a BizTalk Application That Uses the MQSeries Adapter
This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application that uses the MQSeries adapter.  
  
> [!NOTE]
>  The application assumes that you have installed the IBM WebSphere MQ, server component for Windows platforms on the same computer as BizTalk Server. It also assumes that you have not yet created any send ports or receive locations. If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.  
  
 The application is a simple content-based routing application using only a receive location and a send port. The receive location reads from an IBM WebSphere MQ queue. The send port takes the message from the receive location and sends it to a different IBM WebSphere MQ queue.  
  
 To create the application, you have to create the IBM WebSphere MQ queues, set up the BizTalk Server receive location and send port, start the send port and enable the receive location, and put a test message in the queue.  
  
 If you have the required permissions to the IBM WebSphere MQ installation, you can create the IBM WebSphere MQ queues through the adapter dialog boxes, and can skip the next procedure. If you do not have such access, you can create the queues using the IBM WebSphere MQ, client components for Windows platforms Explorer. To create the queues through the IBM WebSphere MQ Explorer snap-in, perform the following procedure.  
  
## To create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer  
 Follow these steps to create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer:  
  
1. Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  
  
2. Double-click **Queue Managers**, and then double-click the default queue manager. The default queue manager is typically named **QM_***<machine_name>* where *machine_name* is the name of your computer.  
  
3. Right-click **Queues**, point to **New**, and then click **Local Queue**.  
  
4. In **Create Local Queue** dialog box, in **Queue Name**, type **BTStoMQS**, and then click **OK**.  
  
5. Right-click **Queues**, point to **New**, and then click **Local Queue**.  
  
6. In **Create Local Queue** dialog box, in **Queue Name**, type **MQStoBTS**, and then click **OK**.  
  
   The next steps create the receive location and the send port, and start the send port and enable the receive location. They also create the IBM WebSphere MQ queues.  
  
## To create the receive location and the MQSeries queue  
 Follow these steps to create the receive location and the MQSeries queue:  
  
1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the default application (**BizTalk Application 1** by default).  
  
2.  Right-click the **Receive Ports** node, click **New**, and select **One-Way Port**.  
  
3.  In the **Receive Port Properties** dialog box, in the **Name** box, type **MQStoBTS**.  
  
4.  In the left pane, click **Receive Locations**, and in the right pane, click **New**.  
  
5.  In the **Receive Location Properties** dialog box, in the **Name** box, type **MQStoBTS**.  
  
6.  Select **MQSeries** from the drop-down list next to the **Type** option.  
  
7.  In the **Transport** section, click **Configure**.  
  
8.  In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **1**.  
  
9. In the **Queue Definition** box, click the ellipsis (**…**) button.  
  
10. In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
11. In the **Queue Manager** box, select the default queue manager.  
  
12. In the **Queue** box, type **MQStoBTS**, and then click **Export**.  
  
13. In the **Export** dialog box, click **Create Queue**,and then click **OK** and **OK** again to return to the **Receive Location Properties** dialog box.  
  
14. In the **Receive Handler** box, select **BizTalkServerApplication**.  
  
15. In the **Receive Pipeline** box, select **PassThruReceive**.  
  
16. Click **OK** to apply changes.  
  
## To create the send port and the MQSeries queue  
 Follow these steps to create the send port and the MQSeries queue:  
  
1.  Right-click **Send Ports**, click **New**, and select **Static One-way Send Port**.  
  
2.  In the **Send Port Properties** dialog box, in the **Name** box, type **BTStoMQS.**  
  
3.  Select **MQSeries** from the drop-down list next to the **Type** option.  
  
4.  In the **Transport** section, click **Configure**.  
  
5.  In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (**…**) button.  
  
6.  In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.  
  
7.  In the **Queue Manager** box, select the default queue manager.  
  
8.  In the **Queue** box, type **BTStoMQS**, and then click **Export**.  
  
9. In the **Export** dialog box, click **Create Queue**, and then click **OK** and **OK** again to return to the **Send Port Properties** dialog box.  
  
10. In the **Send Pipeline** box, select **PassThruTransmit**.  
  
11. Click to select **Filters** in the left pane, and then configure filter options in the right pane.  
  
12. In the **Property** drop-down list, select **BTS.ReceivePortName**.  
  
13. In the **Value** box, type **MQStoBTS**.  
  
14. Click **OK** to apply changes.  
  
## To enable the receive location and start the send port  
 Follow these steps to enable the receive location and start the send port:  
  
1. Right-click the **MQStoBTS** receive location, and then click **Enable**.  
  
2. Right-click the **BTStoMQS** send port, and then click **Start**.  
  
   The next step is to test the application by sending a test message to the receive queue.  
  
## To test the application  
 Follow these steps to test the application:  
  
1. Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.  
  
2. Right-click **MQStoBTS**, and then click **Put Test Message**.  
  
3. In the **Message Data** box, type a test message. Click **OK**.  
  
   After you enter the data, the **Current Depth** for the **MQStoBTS** queue is one (1). When the application processes the message, the count returns to zero (0) and the **Current Depth** for **BTStoMQS** becomes one (1). You can also view the content of the message.  
  
## To view the message  
 Follow these steps to view the message:  
  
1.  Double-click the **BTStoMQS** queue.  
  
2.  Double-click the message, and then select the **Data** sheet. You can view the text of the message in the **Message Data** box.  
  
3.  Click **OK**.  
  
## See Also  
 [What Is the MQSeries Adapter?](../core/what-is-the-mqseries-adapter.md)   
 [MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md)