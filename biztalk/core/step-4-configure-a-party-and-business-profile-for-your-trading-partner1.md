---
title: "Step 4: Configure a Party and Business Profile for Your Trading Partner1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db50d0f6-e838-4e92-8548-a63a2c445d55
caps.latest.revision: 40
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Configure a Party and Business Profile for Your Trading Partner
![Step 4 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-4of9.gif "Step_4of9")  
  
 In this step, you configure a party and business profile for your trading partner Fabrikam to send an 850 message to your organization and receive a 997 acknowledgment message in return.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure a party and business profile for your trading partner  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to **Microsoft BizTalk Server**, and then clicking **BizTalk Server Administration**.  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**. Right-click **Parties**, point to **New**, and then click **Party**.  
  
3. In the **Party Properties** dialog box, enter **Fabrikam** in the **Name** field.  
  
4. Clear the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box. By clearing the check box you specify that the party (in this case, **Fabrikam**) does not host BizTalk Server.  
  
5. Click **OK**.  
  
6. Right-click the party name, point to **New**, and then click **Business Profile**.  
  
7. In the **Profile Properties** dialog box, on the **General** page, enter `Fabrikam_Profile` in the **Name** text box.  
  
   > [!NOTE]
   >  When you create a party, a profile named *PartyName*_Profile is automatically created. You can use this profile instead of creating a new one. To rename a profile, right-click the profile and select **Properties**. In the **General** page, specify a name for the profile.  
  
8. Click **OK**.  
  
## Next Steps  
 You configure the receive location (**fromTHEM_4010_850**) to receive the 850 message from Fabrikam, as described in [Step 5: Configure a Receive Port and Receive Location](../core/step-5-configure-a-receive-port-and-receive-location.md).  
  
## See Also  
 [Configuring EDI Properties](../core/configuring-edi-properties.md)