---
title: "Step 3: Configure a Party and Business Profile for Your Organization2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 024d1ec7-237a-43cb-8159-90f9c71a670e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Configure a Party and Business Profile for Your Organization
![Step 3 of 11](../core/media/tut-step3-of-11.gif "Tut_Step3_of_11")  
  
 In this step, you configure a party and a business profile for your organization to receive an 864 message from your trading partner and return a 997 acknowledgment message and an asynchronous MDN.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure a party and business profile for your organization  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then clicking **BizTalk Server Administration**.  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**. Right-click **Parties**, point to **New**, and then click **Party**.  
  
3. In the **Party Properties** dialog box, enter **Contoso** in the **Name** field.  
  
4. Select the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box. By selecting the check box you specify that the party (in this case, **Contoso**) also hosts BizTalk Server.  
  
5. Click **OK**.  
  
6. Right-click the party name, point to **New**, and then click **Business Profile**.  
  
7. In the **Profile Properties** dialog box, on the **General** page, enter `Contoso_Profile` in the **Name** text box.  
  
   > [!NOTE]
   >  When you create a party, a profile is also created. You can rename and use that profile instead of creating a new one. To rename a profile, right-click the profile and select **Properties**. In the **General** page, specify a name for the profile.  
  
8. Click **OK**.  
  
## Next Steps  
 You configure a party and business profile for your partner organization (**Fabrikam**), as described in [Step 4: Configure a Party and Business Profile for Your Trading Partner](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md).  
  
## See Also  
 [Configuring EDI Properties](../core/configuring-edi-properties.md)