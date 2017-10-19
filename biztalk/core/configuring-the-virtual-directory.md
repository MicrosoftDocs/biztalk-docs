---
title: "Configuring the Virtual Directory | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "virtual directory, configuring"
  - "configuring virtual directory"
ms.assetid: 548e3bee-66bc-424c-895d-e8672a3d6301
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the Virtual Directory
This topic shows the procedures for configuring the virtual directory and verifying the application for a user.  
  
## Configuring the Directory  
  
#### To configure the virtual directory  
  
1.  On the %systemdrive%, create a folder to be configured as a virtual directory.  
  
2.  Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.  
  
3.  Expand **\<server name>** and then expand **Sites**.  
  
4.  Right-click **Default Web Site** and click **Add Virtual Directory**.  
  
5.  In the **Add Virtual Directory** dialog box, type the alias.  
  
6.  Type the path of the folder created in step 1. Alternatively, click **(…)** to browse to the folder location.  
  
7.  Click **OK**. The folder is displayed under the **Default Web Site** folder.  
  
8.  Right-click the folder and click **Convert to Application**.  
  
9. In the **Add Application** dialog box, click **OK**. The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).  
  
## Verifying an Application for a User  
 Internet Information Services (IIS) applications run in high isolation; therefore, you must verify that the application can run in the context of a user in the BizTalk Server Isolated Host Users group by using the following procedure.  
  
#### To verify an application for a user  
  
1.  In Control Panel, open **Administrative Tools**, and then click **Component Services**.  
  
2.  Navigate to the COM+ application in **Component Services**.  
  
3.  Right-click the COM+ application, and click **Properties**.  
  
4.  Click **Identify** and change the identity under which this COM+ application runs to a user that is a member of a BizTalk Server group.  
  
## See Also  
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)