---
title: "Defining Session Settings2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5785ef27-d559-4a45-b8c0-eac646d01842
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Defining Session Settings
Before you can connect to a host, you must define the settings you will need for your session. These settings include the LU or Pool Name and the Host Code Page.  
  
### To define session settings for a Host Integration Server connection  
  
1.  On the **Session** menu, click **Session Configuration**. The **3270 Settings** dialog box appears.  
  
2.  In the **LU or Pool Name** box, select the correct LU or pool name.  
  
3.  In the **Host Code Page** box, select the correct host code page. The default is United States.  
  
4.  Optionally, use a **Script File** to record and playback an automatic logon procedure. For more information, see Recording and Playing Logon Scripts.  
  
5.  Click **OK**.  
  
### To define session settings for a TN3270E connection  
  
1.  On the **Session** menu, click **Session Configuration**. The **3270 Settings** dialog box appears.  
  
2.  Enter the **Server Name or Address**. This should be the IP address of the Host Integration Server running the TN3270 service.  
  
3.  Select the **Model** to use for the connection from the drop down list.  
  
4.  Leave **Device** blank if you want to allow the TN3270 service to select an LU. Optionally, you can enter the name of a specific LU or LU pool.  
  
5.  Enter the **Port** number to use when connecting to the TN3270 service. The default is 23.  
  
6.  In the **Host Code Page** box, select the correct host code page. The default is United States.  
  
7.  Optionally, use a **Script File** to record and playback an automatic logon procedure. For more information, see Recording and Playing Logon Scripts.  
  
8.  Click **OK**.  
  
## See Also  
 [3270 Client](../core/3270-client2.md)