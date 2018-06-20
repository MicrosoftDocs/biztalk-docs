---
title: "Step 5: Configure a Receive Port and Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43fc8d12-5fde-4ddf-a7f0-770f078ba66b
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Configure a Receive Port and Receive Location
![Step 5 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 In this step you configure a receive port and receive location for receiving the 850 message in the folder set up for the Fabrikam party.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure a receive port and receive location for receiving the 850 message  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2. In the Receive Port Properties dialog box, in the **Name** field, enter `ReceiveEDI_fromTHEM_A`.  
  
3. Click **Receive Locations** in the console tree, and then click **New** in the right-hand pane.  
  
4. In the **Receive Location Properties** dialog box, in the **Name** field, enter `fromTHEM_4010_850`.  
  
5. For **Type**, select **FILE**, and then click **Configure**.  
  
   > [!NOTE]
   >  The transport type of the receive location is FILE because the test message is a flat file delivered into a folder.  
  
6. In the **FILE Transport Properties** dialog box, click the **Browse** button next to the **Receive folder** field. In the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM, and then click **OK**.  
  
7. In the **FILE Transport Properties** dialog box, change the **File mask** to **\*.txt** and click **OK**.  
  
   > [!NOTE]
   >  The file mask is set to *.txt because the input test message is a text file, SamplePO.txt.  
  
8. In the **Receive Location Properties** dialog box, in the **Receive Pipeline** field, select **EdiReceive**.  
  
   > [!NOTE]
   >  The receive pipeline used to receive EDI interchanges, except for those delivered over the AS2 transport, is the EdiReceive pipeline. (The AS2EdiReceive receive pipeline is used to receive EDI interchanges delivered over the AS2 transport.)  
  
   > [!NOTE]
   >  If EdiReceive is not listed in the drop-down list for receive pipeline, your application may not have a reference to the BizTalk EDI Application. To add the reference, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
9. Click **OK**, and then click **OK** again.  
  
   > [!NOTE]
   >  The account that has log-on privileges for the BizTalk service should also be granted full access permissions for the receive folder associated with the fromTHEM_4010_850 receive location ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM). If not, you will receive an error when attempting to enable the receive location. To change the access permissions for the receive folder, go to the Security tab in the **Properties** dialog box for that folder in Windows Explorer.  
  
10. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Receive Locations**, right-click **fromTHEM_4010_850**, and then click **Enable**.  
  
## Next Steps  
 You configure the send port (**toOrderSystem**) to send the 850 message to OrderSystem, as described in [Step 6: Configure a Send Port to Send Data to Your Organization](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md).  
  
## See Also  
 [Configuring a Port to Receive EDI Messages and Acknowledgments](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)