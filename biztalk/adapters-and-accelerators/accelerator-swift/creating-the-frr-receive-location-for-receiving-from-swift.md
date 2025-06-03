---
description: "Learn more about: Creating the FRR Receive Location for Receiving from SWIFT"
title: "Creating the FRR Receive Location for Receiving from SWIFT"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Creating the FRR Receive Location for Receiving from SWIFT
To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the SWIFT Network into A4SWIFT.  
  
> [!NOTE]
>  It is advisable to set up two receive locations for receiving messages from SAA: one to receive PAN/NANs and one to receive all other messages. To set up the two receive locations, you must receive messages from two MQSeries queues at SAA: one for PAN/NANs and one for all other message types.  
  
 **Summary**  
  
 Create a receive location with the following properties and components:  
  
|Property/Component|Setting|  
|-------------------------|-------------|  
|Receive port|One-way port|  
|Transport type|MQSeries|  
|Queue Definition (MQSeries)|MQSeries server<br />Queue manager<br />Queue|  
|Receive handler|BizTalkServerApplication|  
|Receive pipeline|The A4SWIFT receive pipeline that you created for FRR|  
  
### To add an FRR receive location for receiving from SWIFT  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and  **BizTalk Application 1** nodes.  
  
2.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
3.  In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRSWIFTReceivePort.  
  
4.  Click **Apply** to bind the port, and then click **OK**.  
  
5.  In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
6.  In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.  
  
7.  In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location, such as FRRSWIFTReceiveLocation.  
  
8.  In the **Transport** section, for the **Type** text box, select **MQSeries**.  
  
9. Click **Configure**.  
  
10. In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis (**…**) button.  
  
11. In the **Queue Definition** dialog box, enter the MQSeries server, queue manager, and queue. Click **OK**.  
  
12. In the **MQSeries Transport Properties** dialog box, verify that the properties are as needed. Click **OK**.  
  
    > [!NOTE]
    >  For more information about MQSeries transport properties, see the MQSeries documentation.  
  
13. In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.  
  
14. For **Receive Pipeline** section, select the A4SWIFT receive pipeline that you created for FRR.  
  
15. Click **Apply**, and then click **OK**  
  
16. In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.
