---
title: "Step 5: Configure the Trading Partner Web Pages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38c3054d-932a-42b6-a821-8b30604d8426
caps.latest.revision: 38
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Configure the Trading Partner Web Pages
![Step 5 of 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")  
  
 In this step, you perform the following tasks to set up trading partner Web pages:  
  
-   Enable the BTS HTTP Receive ISAPI filter that is required for HTTP transport.  
  
-   Set up a folder and an aspx page to route the 997 acknowledgment to the partner organization Fabrikam using HTTP transport. The Fabrikam virtual directory drops the 997 acknowledgment into the \\_997ToFabrikam folder, which is called out in the Destination_URL setting of the 997 send port.  
  
-   Set up the ASPX page to route the original message to the home organization Contoso. The Contoso virtual directory uses BTSHttpReceive.dll to receive the AS2 message and submit it to the receive location.  
  
> [!NOTE]
>  The procedures provided in this topic are for IIS 7.0.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To enable the BTS ISAPI Filter  
  
1. Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. Select the root Web server entry and in the **Features View**, double-click **Handler Mappings** and then in the **Actions** pane, click **Add Script Map**.  
  
   > [!NOTE]
   >  Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites. If you wish to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.  
  
3. In the **Add Script Map** dialog box, enter `BtsHttpReceive.dll` in the **Request path** field.  
  
4. In the **Executable** field, click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive. Select **BtsHttpReceive.dll**, and then click **OK**.  
  
5. Enter `BizTalk HTTP Receive` in the `Name` field, and then click **Request Restrictions**.  
  
6. In the **Request Restrictions** dialog box, select the **Verbs** tab and then select **One of the following verbs**. Enter `POST` as the verb.  
  
7. On the **Access** tab, select **Script**, and then click **OK**.  
  
8. Click **OK** and when prompted to allow the ISAPI extension, click **Yes**.  
  
9. Right-click the BTSHttpReceive.dll entry, and then select **Edit Feature Permissions**.  
  
10. Ensure that **Read**, **Script** and **Execute** are selected, and then click **OK**.  
  
11. Click **Features View**, and then double-click **ISAPI and CGI Restrictions**.  
  
12. Ensure that an entry for BTSHTTPReceive.dll exists, and that **Restriction** is set to **Allowed**.  
  
    > [!NOTE]
    >  The ISAPI and CGI Restriction entry for BTSHTTPReceive.dll is created automatically when you create the script map.  
  
### To configure the Fabrikam Web page  
  
1. In IIS Manager, right-click **Application Pools** and select **Add Application Pool**.  
  
2. In the **Add Application Pool** dialog box, enter **BizTalkAppPool** in **Name**, and then select **.NET Framework V4.0.30210** in the **.NET Framework version** drop-down list. Click **OK**.  
  
   > [!NOTE]
   >  The version number may vary depending on the version of [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installed on the machine.  
  
3. Select **Application Pools**, in the **Features View** select **BizTalkAppPool**, and then click **Advanced Settings** in the **Actions** pane.  
  
4. In the **Advanced Settings** dialog box, set **Enable 32-Bit Applications** to **True**.  
  
   > [!NOTE]
   >  This step is required only on a 64-bit machine if you want IIS to run in a 32-bit mode.  
  
5. Select **Identity** and then click the **ellipsis (…)** button.  
  
6. In the **Application Pool Identity** dialog box, select **Custom account** and then click **Set**.  
  
7. Enter the **User name** and **Password** for a user account that is a member of the administrators group, enter the password in **Confirm password** and then click **OK** three times to return to the IIS Manager.  
  
8. In IIS Manager, open the **Sites** folder. Right-click the **Default Web Site**, and then select **Add Application**.  
  
9. In the **Add Application** dialog box, enter **Fabrikam** in **Alias**, and then click **Select**.  
  
10. In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.  
  
11. Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam for the **Physical path**.  
  
12. Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box. Click **Close**, and then click **OK**.  
  
13. In IIS Manager, select the Fabrikam virtual directory and in **Features View**, double-click **Authentication**.  
  
14. In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**. If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.  
  
### To configure the Contoso Web page  
  
1. In IIS Manager, open the **Sites** folder. Right-click the **Default Web Site** and then select **Add Application**.  
  
2. In the **Add Application** dialog box, enter **Contoso** in **Alias**, and then click **Select**.  
  
3. In the **Select Application Pool** dialog box, select **BizTalkAppPool** and click **OK**.  
  
   > [!NOTE]
   >  The BizTalkAppPool was created previously when configuring the Fabrikam Web page, and should be set to the identity of a user that is a member of the administrators group.  
  
4. Click the **ellipsis (…)** button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.  
  
5. Click **Test Settings** and verify that there are no errors displayed in the **Test Connection** dialog box. Click **Close**, and then click **OK**.  
  
6. In IIS Manager, select the Contoso virtual directory and in the **Features View**, double-click **Authentication**.  
  
7. In **Authentication**, select **Anonymous Authentication** and verify that the **Status** is **Enabled**. If the **Status** is **Disabled**, click **Enable** in the **Actions** pane.  
  
## Next Steps  
 You configure the receive location (**Receive_AS2**) to receive the AS2 message from Fabrikam, as described in [Step 6: Configure the EDI-AS2 Receive Location](../core/step-6-configure-the-edi-as2-receive-location.md).  
  
## See Also  
 [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)
