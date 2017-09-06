---
title: "Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration, building and deploying previous version of BizTalk project for receiving an IDOC"
  - "migrating, building and deploying previous version of BizTalk project for receiving an IDOC"
  - "migration"
ms.assetid: ab6bdf9a-dca5-4acd-97b2-a9afe9792978
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC
![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you build and deploy your existing vPrev BizTalk project to receive an IDOC from an SAP system.  
  
> [!NOTE]
>  You do not need to make any change to the vPrev BizTalk project.  
  
## Prerequisites  
 You must have a vPrev BizTalk project to receive an ORDERS03 IDOC from an SAP system.  
  
### To build and deploy the vPrev BizTalk project  
  
1.  Create a strong-name key file required to build and deploy the solution. To create a strong-name key file, do the following:  
  
    1.  Start Visual Studio Command Prompt.  
  
    2.  At the command prompt navigate to the folder where you want to create the key file. For example, type **cd C:\Sample**, and then press ENTER.  
  
    3.  At the command prompt, type **sn -k \<key file name>.snk**, and then press ENTER.  
  
2.  Right-click the BizTalk solution name in Solution Explorer, and then click **Properties**. In the **Property Pages** dialog box, do the following:  
  
    1.  Click **Configuration Properties** from the left pane, and make sure the check boxes in the **Build** and **Deploy** columns are selected.  
  
    2.  Click **OK**.  
  
3.  Right-click the BizTalk project in Solution Explorer, and then click **Properties**. In the **Property Pages** dialog box, do the following:  
  
    1.  In the left pane, expand **Common Properties**, and then click Assembly.  
  
    2.  In the right pane, under the **Strong name** category, for the **Assembly Key File** property, provide the path to the assembly key file you created earlier.  
  
    3.  Click **OK**.  
  
4.  In Solution Explorer, right-click the solution name, and then click **Build Solution**.  
  
5.  After the solution successfully builds, right-click the solution name, and then click **Deploy Solution**.  
  
## Next Steps  
 Create and configure a WCF-Custom receive port and configure it to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], as described in [Step 2: Configure a WCF-Custom One-way Receive Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md).  
  
## See Also  
 [Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)