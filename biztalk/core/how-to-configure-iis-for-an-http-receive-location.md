---
title: "Configure IIS for an HTTP Receive Location | Microsoft Docs"
description: Create the BTS HTTP Receive application in IIS, and test the application pool settings in BizTalk Server
ms.custom: ""
ms.date: "10/10/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure IIS for an HTTP Receive Location
The HTTP receive location uses an application within Internet Information Services (IIS). This topic lists the steps to enable the HTTP receive location within IIS. 

Depending on your operating system, the steps to configure the IIS application may vary. Use these steps as a guide, as the user interface may be different on your OS.
  
## 32-bit vs 64-bit

An HTTP receive location uses the BTSHTTPReceive.dll. There is a 32-bit and a 64-bit version of the DLL. You choose which version you want to use. 64-bit processes have more available memory, so if you process larger messages, then the 64-bit version may be best. 

**32-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive*.
**64-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive64*

To run the 64-bit version of the HTTP receive adapter in 64-bit native mode,  open a command prompt, and execute the following scripts:  

1. Type: `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  

2. Type: `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid. You can have only one isolated receiver per process.  
  
##  Configure the IIS application
  
1. Open **Internet Information Services** (open **Server Manager**, select **Tools**, and select **Internet Information Services Manager**). 
  
2. In IIS, select your server name. In the **Features View**, double-click **Handler Mappings**. In the Actions pane, select **Add Script Map**.  
  
   > [!NOTE]
   >  When you configure the script mapping at the web server-level, the mapping applies to all web sites. If you want to restrict the mapping to a specific Web site or virtual folder, select that web site or folder, and then add the script map.  
  
3. In **Add Script Map**, select **Request path**, and type `BtsHttpReceive.dll`.  
  
4. In **Executable**, select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive. Select **BtsHttpReceive.dll**, and then select **Open**.  
  
5. In **Name**, enter `BizTalk HTTP Receive`, and then select **Request Restrictions**. In this window:
  
   1. In **Verbs**, select **One of the following verbs**, and enter `POST`.  
  
   2. In **Access**, select **Script**, and then select **OK**.  
  
   3. When prompted to allow the ISAPI extension, select **Yes**.  
  
6. Create a new application pool (right-click **Application Pools**, select **Add application pool**). **Name** your application pool (such as `BTSHTTPReceive`), select **NET Framework v4.0.30319**, and select **OK**.  
  
    > [!NOTE]
    >  The .NET version number may vary depending on the version of .NET Framework installed on the computer.  
  
     The new application pool is listed.  
  
7. Select your new application pool, and open the **Advanced Settings** (**Actions** pane). In this window:

    - **Enable 32-Bit Application**: Set to **True** if you chose the 32-bit **BtsHttpReceive.dll**
    - **Process Model** section, **Identity**: Select the ellipsis (**…**), select **Custom account**, and then **Set** it to an account that is a member of the **BizTalk Isolated Host Users** and **IIS_WPG** groups. Select **OK**. 
  
8. Add a new application to the web site (right-click the **Default Web Site**, select **Add Application**). In this window:
  
   1. **Alias** : Enter an alias that you associate with the application (such as `BTS HTTP Receive`, and then **Select**.  
   2. Select the new application pool you just created, and then select **OK**.  
   3. **Physical path**: Select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.  
   4. **Test Settings** to verify there are no errors in the **Test Connection** dialog box. **Close**, and then select **OK**.  
  
      > [!TIP]
      > If Test Settings returns a warning, the identity of the application pool may be missing permissions to a folder, or access to a group. As a troubleshooting step, select **Connect As**, enter the **User name** and **Password** for a user account that is a member of the Administrators group. 

9. The new application appears is listed under **Default Web Sites**.  
  
## See Also  
 [How to Configure an HTTP Receive Location](../core/how-to-configure-an-http-receive-location.md)
