---
title: "Creating the FRR Send Ports for Sending to the Custom Handlers | Microsoft Docs"
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
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating the FRR Send Ports for Sending to the Custom Handlers
To perform FIN Response Reconciliation, you need to create a series of send ports, each of which sends a message (original message or response) from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the custom handlers that process the correlated messages.  

 **Summary**  

 Create a series of send ports with the following properties and components, each one distinguished by the value of BTS.Operation in the filter:  


|        Property/Component        |                                             Setting                                              |
|----------------------------------|--------------------------------------------------------------------------------------------------|
|            Send port             |                                       Static one-way port                                        |
|          Transport type          |                                               FILE                                               |
| Destination folder (Address URI) |                         The folder that you want to send the message to                          |
|     File name (Address URI)      |                                         %MessageID%.txt                                          |
|          Send pipeline           | [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].BizTalk.DefaultPipelines. PassThruTransmit |
|             Filters              |                                   As shown in the tables below                                   |

 The send ports for the different messages are distinguished by the value of BTS.Operation in the send port's filter.  

### To add FRR send ports for sending to the custom handlers  

1.  In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.  

2.  In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRCustomHandlersSendPort.  

3.  For **Type**, select **FILE**.  

4.  Click **Configure**.  

5.  In the FILE Transport Properties dialog box, click **Browse**.  

6.  In the Browse For Folder dialog box, move to the folder that you want to send messages from. Click **OK**.  

    > [!NOTE]
    >  If this folder does not exist, you can create it using the **Make New Folder** command.  

7.  In the **File name** box, type **%MessageID%.txt**, and then click **OK**.  

    > [!NOTE]
    >  You can create a different folder for each type of message.  

8.  In the Send Port Properties dialog box, for Send handler, verify that **BizTalkServerApplication** is selected.  

9. For **Send Pipeline**, select **PassThruTransmit**.  

10. Click **Filters** in the left pane, and then do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **A4SWIFT_FrrService**.|  
    |**Group**|**And**|  
    |**Property**|Select **BTS.Operation**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type one of the BTS.Operation values from the table below.|  

     For BTS.Operation, enter one of the following values:  

    |Message type|BTS.Operation value|  
    |------------------|-------------------------|  
    |All Category 0 to 9 SWIFT FIN message types|**A4SWIFT_FrrSendMTMsg**|  
    |MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)|**A4SWIFT_FrrSendTransport**|  
    |MT010 (Non-Delivery Warning)|**A4SWIFT_FrrSend010NDW**|  
    |MT011 (Delivery Notification)|**A4SWIFT_FrrSend011Delivered**|  
    |MT012 (Sender Notification)|**A4SWIFT_FrrSend012SenderACK**|  
    |MT015 (DNK, or Delayed NAK)|**A4SWIFT_FrrSend015DNK**|  
    |MT019 (Abort Notification)|**A4SWIFT_FrrSend019Abort**|  
    |MTS21_FIN_ACKNAK (Acknowledgment of a FIN message sent by an LT (ACK)|**A4SWIFT_FrrSendS21ACK**|  
    |MTS21_FIN_ACKNAK (Negative acknowledgment of a FIN message sent by an LT (NAK)|**A4SWIFT_FrrSendS21NAK**|  

11. For Category 0 to 9 SWIFT FIN messages that are not successfully sent, do the following in the **Filters** pane:  

    > [!NOTE]
    >  The **A4SWIFT_FRRFailedReason** properties in the following filter should be grouped.  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **A4SWIFT_FrrService**.|  
    |**Group**|**And**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **True**.|  
    |**Group**|**And**|  
    |**Property**|Select **BTS.Operation**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **A4SWIFT_FrrSendMTMsg**.|  
    |**Group**|**And**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type *\<NAKErrorCode\>*, such as "Y01".|  
    |**Group**|**Or**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **TimedOut**.|  
    |**Group**|**Or**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **TransportError**.|  
    |**Group**|**Or**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **DelayedNAK**.|  
    |**Group**|**Or**|  
    |**Property**|Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.|  
    |**Operator**|Select **==**.|  
    |**Value**|Type **AbortMessage**.|  

12. Click **Apply**, and then click **OK**.  

13. Right-click the send port, and then click **Start**.  

14. Repeat steps 2 through 13 to create a send port for each message type required.