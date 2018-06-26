---
title: "Step 6: Configure the EDI-AS2 Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Configure the EDI-AS2 Receive Location
![Step 6 of 11](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")  
  
 In this step, you set up a one-way receive location that receives the EDI message from the Fabrikam party. This receive location uses the AS2EdiReceive receive pipeline to process the incoming EDI/AS2 message. The message will be sent to the receive location by the sender.exe application through the Contoso virtual directory using the BTSHTTPReceive.dll ISAPI extension.  
  
 In this tutorial, you will set up a dynamic send port to send the MDN response asynchronously. In this scenario, only a one-way receive port is required. However, you could also change Sender.exe to send an AS2 message specifying a synchronous MDN. You would then have to create a two-way request response receive port to return the MDN. For more information, see the "To test the solution" section of [Walkthrough (AS2): Receiving EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md).  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To create the BizTalk HTTP receive location  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2. Name the receive port as **Receive_AS2**.  
  
3. Click **Receive Locations** in the console tree, and then click **New**.  
  
4. In the **Receive Location Properties** dialog box, name your receive location **Receive_AS2**, select **HTTP** for **Type**, and then click **Configure**.  
  
5. In the **HTTP Transport Properties** dialog box, enter **/Contoso/BTSHTTPReceive.dll** for **Virtual directory plus ISAPI extension**. Clear **Return correlation handle on success** and select **Suspend failed requests**. Click **OK**.  
  
6. Select **AS2EdiReceive** for the **Receive Pipeline**. Click **OK**, and then click **OK** again.  
  
   > [!NOTE]
   >  The AS2EdiReceive receive pipeline performs AS2 decoding and EDI disassembly.  
  
7. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations** under the BizTalk Application 1 node, right-click **Receive_AS2**, and then click **Enable**.  
  
## Next Steps  
 You configure the send port (**Send_Asynch_MDN**) send port to send the asynchronous MDN back to Fabrikam, as described in [Step 7: Configure the MDN Send Port](../core/step-7-configure-the-mdn-send-port.md).  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)   
 [Configuring a Receive Port for Messages over AS2](../core/configuring-a-receive-port-for-messages-over-as2.md)