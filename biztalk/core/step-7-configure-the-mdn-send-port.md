---
title: "Step 7: Configure the MDN Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 983033ac-9d32-47c8-9bb8-b4161bcdf183
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Configure the MDN Send Port
![Step 7 of 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")  
  
 In this step, you set up a dynamic send port to send an asynchronous MDN to the \\_MDNToFabrikam folder. This send port uses the AS2Send send pipeline to generate the outgoing MDN response. Since this is a dynamic send port, it will use the address in the Receipt-Delivery-Option line in the header of the message to route the message to the \\_MDNToFabrikam folder. That address is the Fabrikam virtual directory. The Default.aspx.cs file associated with that virtual directory builds the MDN with an .msg extension, and sends the file to the destination folder (which is also specified in Receipt-Delivery-Option).  
  
> [!NOTE]
>  You can also configure the agreement to send the MDN to another address, by overriding the message settings with the agreement settings. For more information, see  
  
 In this example the MDN is sent using a dynamic send port; however you can also use a static send port to send the MDN to a static address. For more information, see [Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md) and [Configuring a Dynamic Send Port for Asynchronous MDNs over AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md).  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To create the Send_Async_MDN send port  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Dynamic One-way Send Port**.  
  
2. In the **Send Port Properties** dialog box, name the send port as **Send_Async_MDN**.  
  
3. Select **AS2Send** for **Send pipeline**.  
  
   > [!NOTE]
   >  The AS2Send pipeline is used because no EDI processing is required for the MDN.  
  
4. Click **Filters** in the console tree. In the Filters pane, select **EdiIntAS.IsAS2AsynchronousMdn** for **Property**, **==** for **Operator**, and enter **True** for **Value**.  
  
   > [!NOTE]
   >  This filter ensures that the dynamic send port only picks up asynchronous MDNs from the MessageBox.  
  
5. Click **OK**.  
  
6. In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send_Async_MDN**, and then click **Start**.  
  
## Next Steps  
 You configure the send port (**Send_Async_997**) to send the 997 acknowledgement back to Fabrikam, as described in [Step 8: Configure the 997 Send Port](../core/step-8-configure-the-997-send-port.md).  
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)   
 [Configuring a Static Send Port for Asynchronous MDNs over AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)   
 [Configuring a Dynamic Send Port for Messages over AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)