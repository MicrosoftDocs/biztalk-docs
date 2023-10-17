---
description: "Learn more about: How to Deploy the BizTalk Server Application"
title: "How to Deploy the BizTalk Server Application2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61db00f5-3ca8-4917-b65f-5644635761f6
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Deploy the BizTalk Server Application
After a developer has created and exported an application for the BizTalk Adapter for Host Applications, an IT professional can import it, update the connection properties, and deploy the application.  
  
 Before you import the application, you can find more information by completing the Importing Exported Packages tutorial. After you complete these procedures, you can perform any application-specific deployment tasks as necessary.  
  
### To import the BizTalk Server application  
  
1.  In the BizTalk Server Administration console, expand the **BizTalk Server 2006 Administration** node.  
  
2.  Expand the **BizTalk Group** node.  
  
3.  Right-click the **Applications** node, click **Import**, and then click **MSI file**.  
  
     This starts the Import MSI Wizard.  
  
4.  Follow the instructions in the wizard. If you need help, you can click **Help** on each wizard page.  
  
### To update the connection properties  
  
1.  In the TI Manager Console, expand the **Remote Environments** folder.  
  
2.  Right-click the **Remote Environment** for this application, and then click **Properties**.  
  
    -   If you have a TCP/IP connection, select the **TCP/IP** tab, and either confirm or enter the appropriate information in the **IP/DNS Address** and **Port** fields.  
  
    -   If you have an SNA connection, select the **LU6.2** tab, and either confirm or enter the appropriate information in the **Local LU Alias**, **Remote LU Alias**, and **Mode Name** fields.  
  
         You may have to obtain this information from your Mainframe or System Administrator.  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)   
 [BizTalk Adapter for Host Applications](../core/biztalk-adapter-for-host-applications2.md)
