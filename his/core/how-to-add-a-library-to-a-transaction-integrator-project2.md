---
description: "Learn more about: How to Add a Library to a Transaction Integrator Project"
title: "How to Add a Library to a Transaction Integrator Project2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2641289e-f90a-4af5-ac20-905e985ab3c5
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Add a Library to a Transaction Integrator Project
Once you have created the Transaction Integrator (TI) project, you need to add an assembly to the project. Once you have added the assembly, you can import a host file definition.  
  
### To add a library to a TI project  
  
1.  Click **Project**, and then click **Add .NET Client Library**.  
  
2.  On the Add New Item dialog, in the Templates pane, confirm that .NET Client Library is highlighted.  
  
3.  In the **Name:** field, type the name of the assembly, and then click **Add**.  
  
4.  On the Welcome to the .NET Client Library Wizard page, click **Next**.  
  
5.  On the Remote Environment page, select the information that describes the remote environment your application will interact with, and then click **Next**.  
  
     Visual Studio will use this information to optimize your application for the specified remote environment. In contrast, the information you entered in Transaction Manager will be used by Host Integration Server when making a connection.  
  
6.  On the Completing the .NET Client Library Wizard page, confirm that the displayed settings are correct, and then click **Create**.  
  
## See Also  
 [Creating an Application with Host Integration Server Designer](../core/creating-an-application-with-host-integration-server-designer1.md)
