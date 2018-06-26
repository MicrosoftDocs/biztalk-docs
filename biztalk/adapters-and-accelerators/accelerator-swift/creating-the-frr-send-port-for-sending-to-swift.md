---
title: "Creating the FRR Send Port for Sending to SWIFT | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, send ports"
  - "send ports, creating"
  - "FRR, creating send ports"
ms.assetid: 1ad766db-d1da-437a-a520-a3b04f0695c4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating the FRR Send Port for Sending to SWIFT
To perform FIN Response Reconciliation, you need to create a send port that sends a message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Network.  

 **Summary**  

 Create a send port with the following properties and components:  


|     Property/Component      |                                                               Setting                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
|          Send port          |                                                         Static one-way port                                                          |
|       Transport type        |                                                               MQSeries                                                               |
| Queue Definition (MQSeries) |                                                 MQSeries server Queue manager Queue                                                  |
|        Send pipeline        | The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR |
|           Filters           |                                                     As shown in the table below                                                      |

### To add a custom send port for sending to SWIFT  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.  

2. In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRSWIFTSendPort.  

3. For **Type**, select **MQSeries**.  

4. Click **Configure**.  

5. In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis () button.  

6. In the Queue Definition dialog box, enter the MQSeries server, queue manager, and queue. Click **OK**.  

7. In the MQSeries Transport Properties dialog box, verify that the properties are as needed. Click **OK**.  

   > [!NOTE]
   >  For more information about MQSeries transport properties, see the MQSeries documentation.  

8. In the Send Port Properties dialog box, for **Send handler**, verify that BizTalkServerApplication is selected.  

9. For **Send Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR.  

10. Click **Filters** in the left pane, and then do the following:  


    |   Use this   |                            To do this                             |
    |--------------|-------------------------------------------------------------------|
    | **Property** |  Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.  |
    | **Operator** |                          Select **==**.                           |
    |  **Value**   |                          Type **False**.                          |
    |  **Group**   |                          Select **And**.                          |
    | **Property** | Type **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**. |
    | **Operator** |                          Select **==**.                           |
    |  **Value**   |                          Type **True**.                           |


11. Click **Apply**, and then click **OK**.  

12. Right-click the send port, and then click **Start**.
