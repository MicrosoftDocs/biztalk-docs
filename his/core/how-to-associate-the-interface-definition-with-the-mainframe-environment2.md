---
title: "How to Associate the Interface Definition with the Mainframe Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92ac8403-4a60-4171-a9fc-99d9cc641aa2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Associate the Interface Definition with the Mainframe Environment
After you create a BizTalk project for your application that uses the BizTalk Adapter for Host Applications, and then add the .xsd file to the project, you must identify your target mainframe, and then associate the interface definition with the mainframe environment.  
  
### To configure the remote environment using TI Manager  
  
1.  Start TI Manager.  
  
2.  Double-click **Transaction Integrator** in the console tree.  
  
3.  Right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.  
  
4.  Use the New Remote Environment Wizard to describe the environment on your target mainframe.  
  
     For more information about how to use the Remote Environment Wizard, see [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)  
  
### To administer the TI .NET assembly metadata using TI Manager  
  
1.  Start TI Manager.  
  
2.  Double-click **Transaction Integrator** in the console tree.  
  
3.  In the **Windows-Initiated Processing** node, right-click **Objects**, point to **New**, and then click **Object**.  
  
4.  Use the Object Wizard to associate the TI assembly that you created earlier with the remote environment of your target mainframe.  
  
     For more information about how to use the Object Wizard, see [Object Wizard (for WIP)](../core/object-wizard-for-wip-2.md).  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)   
 [Creating a BizTalk Application](../core/creating-a-biztalk-application1.md)   
 [How to Export the Schema](../core/how-to-export-the-schema1.md)