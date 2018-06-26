---
title: "Step 8: Configure the 997 Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4780c491-9f1a-4f13-b346-6a2e1801ec09
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: Configure the 997 Send Port
![Step 8 of 11](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")  
  
 In this step, you set up a send port to send the 997 message to the partner. This send port uses the AS2EdiSend send pipeline to transport an EDIINT/AS2-encoded 997 acknowledgment to the _997ToFabrikam folder.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To create the Send_Async_997 send port  
  
1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
   > [!NOTE]
   >  You will use a static one-way send port because no MDN has been set up for the Fabrikam party as an AS2 message receiver.  
  
2. In the **Send Port Properties** dialog box, name your send port **Send_Async_997**. Select **HTTP** for **Type**, and then click **Configure**.  
  
3. In the **HTTP Transport Properties** dialog box, for **Destination URL**, enter `http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`. Clear **Enable chunked encoding** and then click **OK**.  
  
   > [!NOTE]
   >  The **Destination URL** setting ensures that the send port will send the 997 message to the Fabrikam virtual directory. The Default.aspx.cs file associated with that virtual directory builds the 997 with an .msg extension, and sends it to the destination folder.  
  
4. In the **Send Port Properties** dialog box, select **AS2EdiSend** for **Send Pipeline**.  
  
5. Click **Filters** in the console tree. For **Property**, select **BTS.MessageType**. For **Operator**, select **==**. For **Value**, enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.  
  
   > [!NOTE]
   >  This filter ensures that the send port will only pick up 997 acknowledgments from the MessageBox.  
  
6. Click **OK**.  
  
7. In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Async_997** send port, and then click **Start**.  
  
## Next Steps  
 You configure the send port (**Send_Payload_EdiXml**) to send the EDI payload to Contoso, as described in [Step 9: Configure the EDI Payload Send Port](../core/step-9-configure-the-edi-payload-send-port.md).  
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)   
 [Configuring a Static Send Port for Messages over AS2](../core/configuring-a-static-send-port-for-messages-over-as2.md)