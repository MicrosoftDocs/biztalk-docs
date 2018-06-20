---
title: "Step 2: Update and Deploy the Tutorial Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d03adfdd-1160-4e8c-a564-3acb2ecd0476
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Update and Deploy the Tutorial Solution
![Step 2 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")  
  
 In this step you update the solution provided for this tutorial, and then build and deploy the tutorial assembly. For the purposes of this tutorial, the necessary schema, custom send pipeline, and map have already been created. The map is used to convert the 850 EDI data into the format required by your Order System.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To enable the EDI Inbound Processing solution to be built in Visual Studio  
  
1. Start **Microsoft Visual Studio** as an administrator.  
  
   > [!CAUTION]
   >  If you do not start Visual Studio with administrator privileges, you will get an error while deploying the solution to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2. In Visual Studio, click **File**, point to **Open**, and then click **Project/Solution**. Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial, select **EDI Inbound Processing.sln**, and then click **Open**.  
  
   > [!NOTE]
   >  This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations. If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
3. Right-click the **Inbound_EDI** project in the Solution Explorer, and then select **Properties**.  
  
4. In the console tree of the **Inbound_EDI Property Pages** dialog box, select  **Deployment** and in the **Server** field ensure that your computer name is entered.  
  
5. In the console tree, click **Signing** and then select **Sign the assembly**. For **Choose a strong key name file**, select \<**New…**\> and enter  **keyfile.snk** as the **Key file name**. Clear **Protect my key file with a password** and then click **OK**.  
  
6. Close the **Inbound_EDI Property Pages** dialog box.  
  
### To deploy the project  
  
1. In Solution Explorer, double-click the **X12_00401_850.xsd** schema. Confirm that it opens.  
  
2. In Solution Explorer, double-click the **Inbound4010850_to_OrderFile.btm** map. Confirm that it opens.  
  
   > [!NOTE]
   >  The Inbound4010850_to_OrderFile.btm map in the project maps the data in the inbound 850 test message to the outbound XML file delivered to the OrderSystem folder (\toOrderSystem).  
  
3. In Solution Explorer, right-click the **Inbound_EDI** project and select **Build** to build the project.  
  
4. In Solution Explorer, right-click the **Inbound_EDI** project and select **Deploy** to deploy the project.  
  
5. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, \<**All Artifacts**\> and then select **Resources**. Verify that the **Inbound_EDI** assembly is listed.  
  
## Next Steps  
 You configure a party and business profile for your organization (**OrderSystem**), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
## See Also  
 [Step 1: Prepare for the EDI Interface Developer Tutorial](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)