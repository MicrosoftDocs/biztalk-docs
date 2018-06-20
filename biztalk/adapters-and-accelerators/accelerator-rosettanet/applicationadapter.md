---
title: "ApplicationAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f9b876b-cd37-4e24-a476-186adc155ac0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ApplicationAdapter
The ApplicationAdapter sample demonstrates how to send notifications from the public and private processes (responder or initiator) when you receive a message. You can customize the sample with whatever additional functionality you want.  
  
 The ApplicationAdapter sample demonstrates how to implement the `IApplicationAdapter` interface to the `ApplicationAdapter1` class. This class includes two methods, `BeginNotify` and `Notify`. The parameters for each class are the message category, source party name, destination party name, Partner Interface Process (PIP) code, PIP instance ID, and PIP version.  
  
 You set the ApplicationAdapter for an agreement by entering the assembly name and class name on the **General** tab of the agreement in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console. The application adapter .dll file runs under the same credentials as the BizTalk host service.  
  
 If you change the ApplicationAdapter sample or any external environment variable that the ApplicationAdapter sample depends on, restart the BizTalk host service that hosts the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public process.  
  
 The ApplicationAdapter sample code is located at \<*drive*\>:\Program Files\ BizTalk \<version\> Accelerator for RosettaNet\SDK\ApplicationAdapter\\.  
  
## Demonstrates  
 The ApplicationAdapter sample demonstrates how to notify the responder private process that the public process has received a message. The notification indicates the message category, the source party name, the destination party name, the PIP code, the PIP version, and the PIP instance ID. You can send this notification for either an action or a response message.  
  
 The `BeginNotify` and `Notify` methods work as follows:  
  
1.  The responder public process receives a message.  
  
    > [!NOTE]
    >  The following steps are also applicable for the scenario in which the public initiator receives a response message from the responder.  
  
2.  If validation by the receive pipeline and public process, and validation adapter, if applicable, was successful, the responder public process calls the `BeginNotify` method in the `ApplicationAdapter` class. This method notifies the responder private process that the public process has received the new message and saved the message in the MessageBox database.  
  
3.  The responder public process sends a signal message back to the initiator.  
  
4.  The responder public process sends the message service content to the responder private process.  
  
5.  The responder private process puts the message in the MessagesToLOB table of the BTARNDATA database.  
  
6.  The responder private process calls the `Notify` method in the `ApplicationAdapter` class to send the End Notify message back to the responder public process. The responder public process must receive the End Notify message for the process to be successfully completed. Otherwise, the message is suspended.  
  
> [!NOTE]
>  You can use the `Notify` message to signal the line-of-business (LOB) application that the message is waiting in the MessagesToLOB table. As soon the system alerts the LOB application, the LOB application can retrieve the message from that table.  
  
## To Implement this Sample  
 To implement the ApplicationAdapter sample, you must add the application adapter to the agreement.  
  
#### To add the application adapter to an agreement  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] **BizTalk \<version\> Accelerator for RosettaNet**, and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and click **Agreements**.  
  
3. Double-click the agreement to which you want to add the application adapter.  
  
4. In the **Application Adapter** box, click the ellipsis button (**...**) button to the right of **Assembly name**, move to the location that contains the application adapter assembly, select the appropriate .dll file, and then click **Open**.  
  
5. Click the down arrow for **Class Name**, select the application adapter class, and then click **OK**.  
  
## See Also  
 [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)