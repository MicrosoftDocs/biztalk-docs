---
title: "Defining Session Settings (5250)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84e88daa-dbf1-40bb-a6ec-5c7eee8e66ef
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Defining Session Settings (5250)
Before you can connect to an AS/400 system, you must define the settings you will need for your 5250 session such as the Local LU Alias, Remote APPC LU Alias, Host Code Page, and Display Size. You can also change the Device Name, although this is generally not necessary.  
  
 **To define basic session settings for the 5250 Client for a Host Integration Server**  
  
1. On the **Session** menu, click **Session Configuration**. The 5250 Session Information dialog box appears.  
  
2. Select the Server Type:  **Host Integration Server**.  
  
3. In the **Local APPC LU Alias** box, type the Local LU Alias provided by your system administrator. In some cases, the Local LU Alias provided by your system administrator may be the same as your user name. In other cases, your system administrator may instruct you to leave the box blank; this allows the Host Integration Server to use the default local LU configured for your user name.  
  
4. In the **Remote APPC LU Alias** box, select the system name of the AS/400, as provided by your system administrator. Your system administrator may instruct you to leave the box blank; this allows the Host Integration Server to use the default system name (also called the remote LU) configured for your user name.  
  
5. In the **Host Code Page** box, select the correct host code page. The default is English-US.  
  
6. Under **Display Size**, select the option button for the correct display size. The default is 24 x 80.  
  
7. To specify a device name other than the default, in the **Device Name** box, type the correct device name.  
  
8. Select the **System 36 Compatibility** check box to connect to a System 36 computer.  
  
9. Select the **Automatic Logon** check box to use the single sign-on feature. You must install the Enterprise Single Sign-On feature to enable single sign-on.  
  
10. Click **OK**.  
  
    **To define basic session settings for the 5250 Client for a TN 5250 Server**  
  
11. On the **Session** menu, click **Session Configuration**. The 5250 Session Information dialog box appears.  
  
12. Select the Server Type:  **TN 5250**.  
  
13. Enter the Server Name or IP Address for the server where Host Integration Server is installed. If you are unsure, see your system administrator.  
  
14. Select a **Terminal Type** from the list box to allow the TN5250 Service to accept client requests from TN5250 clients emulating those types of terminals. Clear a name to cause TN5250 Service to reject requests from clients emulating that terminal type. All terminal names are selected by default.  
  
15. Select **Use Default** to use the port number configured with the service (on the **Host Integration Server Service Properties** page).  
  
16. You can override the default value for a given session by selecting Use and typing another port number.  
  
     Note that TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client to connect to multiple host computers. See the Host Integration Server help for more information.  
  
17. In the **Host Code Page** box, select the correct host code page. The default is English-US.  
  
18. Click **OK**.  
  
## See Also  
 [5250 Client](../core/5250-client1.md)