---
title: "Step 1: Prepare for the AS2 Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3421c33b-0ccd-4e9d-b1c3-b161278e4d98
caps.latest.revision: 39
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Prepare for the AS2 Tutorial
![Step 1 of 11](../core/media/tut-step1-of-11.gif "Tut_Step1_of_11")  
  
 The AS2 tutorial is run on a single computer. To prepare for the tutorial, you must install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as described in [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) section. You must also add a reference to the BizTalk Server EDI Application as described in this topic. The files required for the AS2 tutorial are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.  
  
> [!NOTE]
>  For this tutorial to work, you need to use the same logon account for both the in-process host instance and the isolated host instance.  
  
> [!NOTE]
>  For this tutorial to work, the BizTalk Server host that is used for this tutorial must be marked as 32-bit.  
  
> [!NOTE]
>  For this tutorial to work, it must be run on a platform using IIS 7.0 or IIS 7.5, and the Enable 32-Bit Application Setting for the Application Pools must be set to True.  
  
 The AS2 tutorial folders include three folders that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will write test output files to (the EDI payload, 997, and MDN). These folder have already been created, but you must set the security permissions for two of the 997 and MDN folders (see the procedure below).  
  
 The folders and files required for the tutorial are as follows:  
  
|Folder\File|Purpose|  
|------------------|-------------|  
|\\_997ToFabrikam|This empty folder will receive the 997 acknowledgment message returned after EDI processing. The folder simulates the application originating the EDI message at the Fabrikam party.|  
|\\_EDIXMLToContoso|This empty folder will receive the XML payload file after BizTalk Server has processed the EDI message. This folder simulates the line-of-business application that is the final destination of the EDI payload.|  
|\\_MDNToFabrikam|This empty folder will receive the MDN message returned from BizTalk Server after AS2 processing. The folder simulates an application at the Fabrikam party.|  
|\Fabrikam|This folder contains the Default.aspx file that saves the 997 into the _997ToFabrikam folder and saves the MDN into the _MDNToFabrikam folder.|  
|\Schemas|This folder contains the X12_00401_864.xsd schema and other schemas that BizTalk uses to process the EDI message. The folder also contains the Schemas.btproj project that you will build and deploy in order to deploy the schemas.|  
|\Sender|This folder contains the Sender.csproj project that you will build and compile to create Sender.exe, which you use to send the X12_00401_864.edi test message (in the \AS2 Tutorial folder) and to return the MDN.|  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
## Procedures  
  
#### To set the security permission for the 997 and MDN folders  
  
1. In Windows Explorer, move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam folder. Right-click the \\_997ToFabrikam folder, and then click **Properties**.  
  
2. Click the **Security** tab, and then click **Edit**. In the **Permissions** dialog box, click **Add**.  
  
3. In the **Select Users, Computers, Service Accounts, or Groups** dialog box, in the object names pane, enter `Everyone`, and then click **OK**.  
  
4. Select **Everyone** in the **Group or user names** box, click the check box for **Write** (under the **Allow** column) in the **Permissions** pane, and then click **OK**.  
  
5. Click **OK**.  
  
6. Repeat these steps for the \\_MDNToFabrikam folder.  
  
#### To mark the BizTalk Server Host as 32-Bit  
  
1. > [!NOTE]
   >  The AS2 pipelines can only be used in a 32-bit process. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit operating system, the following steps must be performed to mark the host processes as 32-bit only.  
  
    Select **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, select **Platform Settings**, and then select **Hosts**.  
  
3. In the details pane, right-click the in-process host you want to use for this tutorial and then select **Properties**.  
  
4. In the **Host Properties** dialog box, on the **General** tab, select **32-bit only**, and then click **OK**.  
  
5. Repeat steps 3-4 for the isolated host.  
  
   If BizTalk Server is installed on a 64-bit operating system, you must also set IIS to run in 32-bit mode when using a 32-bit BizTalk host process. The instructions for setting IIS are presented within [Step 5: Configure the Trading Partner Web Pages](../core/step-5-configure-the-trading-partner-web-pages.md), as IIS allows you to set the 32-bit worker process on a per application pool basis.  
  
#### To add reference to the BizTalk EDI Application  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **Applications** node, right-click the application that you want to use for EDI, such as BizTalk Application 1. Point to **Add**, and then click References.  
  
2. In the **Add Application Reference** dialog box, select **BizTalk EDI Application**, and then click **OK**.  
  
## Next Steps  
 You deploy the sample X12 schema as described in [Step 2: Create and Deploy the Sample X12 Schema](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
## See Also  
 [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)