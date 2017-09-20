---
title: "How to Configure IIS for an HTTP Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64-bit support, HTTP adapters"
  - "HTTP adapters, IIS"
  - "configuring [HTTP adapters], IIS"
  - "receive locations, IIS"
  - "IIS, receive locations"
  - "HTTP adapters, 64-bit support"
  - "IIS, HTTP adapters"
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure IIS for an HTTP Receive Location
Depending on which version of Microsoft Windows you are using, you will have to configure Microsoft Internet Information Services (IIS) differently to work with the HTTP adapter receive location.  
  
 If your operating system is [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], IIS 7.0 provides two different application isolation modes to protect Web applications. Worker process isolation mode is the default mode. You can configure the HTTP adapter receive location to work with either mode, but worker process isolation mode is recommended for its improved security functionality.  
  
> [!NOTE]
>  If your operating system is the x64 edition of [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], the 64-bit version of the HTTP receive adapter is installed to the *\<drive>***\Program Files (x86)\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\HttpReceive64** directory of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by default. To run the 64-bit version of the HTTP receive adapter in 64-bit native mode you must execute the following script from a command line:  
>   
>  `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  
>   
>  `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid. You can have only one isolated receiver per process.  
  
### To configure the IIS 7.0 worker process isolation mode to work with the HTTP adapter receive location  
  
1.  Click **Start**, point to **Settings**, and then click **Control Panel**.  
  
2.  In Control Panel, double-click **Administrative Tools**.  
  
3.  In Administrative Tools, double-click **Internet Information Services**.  
  
4.  In Internet Information Services, select the root Web server entry. In the **Features View**, double-click **Handler Mappings**, and then in the Actions pane, click **Add Script Map**.  
  
    > [!NOTE]
    >  Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites. If you want to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.  
  
5.  In the **Add Script Map** dialog box, in the **Request path** field, type `BtsHttpReceive.dll`.  
  
6.  In the **Executable** field, click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive. Select **BtsHttpReceive.dll** and then click **OK**.  
  
7.  In the **Name** field, type `BizTalk HTTP Receive`, and then click **Request Restrictions**.  
  
8.  In the **Request Restrictions** dialog box, click the **Verbs** tab and then select **One of the following verbs**. Enter `POST` as the verb.  
  
9. On the **Access** tab, select **Script**, and then click **OK**.  
  
10. When prompted to allow the ISAPI extension, click **Yes**.  
  
11. Right-click **Application Pools**, point to **New**, and then click **Application pool**.  
  
12. In the **Add Application Pool** dialog box, in the **Name** box, type a name for the application pool. Select **NET Framework v4.0.30319** and then click **OK**.  
  
    > [!NOTE]
    >  The version number may vary depending on the version of .NET Framework installed on the computer.  
  
     The new application pool appears in the list of **Application Pools**.  
  
13. In **Application Pools**, in the **Features View**, select the new application pool, and then click **Advanced Settings** in the Actions pane.  
  
14. In the **Advanced Settings** dialog box, in the **Process Model** section, in the **Identity** field, click the ellipsis (**…**) button.  
  
15. In the **Application Pool Identity** dialog box, select **Custom account**, and then click **Set**. Click **OK** to close the **Advanced Settings** dialog box.  
  
16. In IIS Manager, open the **Sites** folder. Right-click the **Default Web Site** and then click **Add Application**.  
  
17. In the **Add Application** dialog box, in **Alias**, enter an alias to associate with the application, and then click **Select**.  
  
18. In the **Select Application Pool** dialog box, select the new application pool you created earlier, and then click **OK**.  
  
19. Click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.  
  
20. Click **Connect As** and enter the **User name** and **Password** for a user account that is a member of the Administrators group, and then click **OK**.  
  
21. Click **Test Settings** and verify that no errors are displayed in the **Test Connection** dialog box. Click **Close**, and then click **OK**.  
  
22. The new application appears in the list of **Default Web Sites** in Internet Information Services (IIS) Manager.  
  
## See Also  
 [How to Configure an HTTP Receive Location](../core/how-to-configure-an-http-receive-location.md)