---
title: "Step 2: Creating the Fabrikam LOBWebApplication | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, creating LOBWebApplication"
  - "LOBWebApplication"
ms.assetid: 2ff8bd20-7fbc-4e16-b177-bb4afac7f7c3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Creating the Fabrikam LOBWebApplication
In this step, you create the LOB application that Fabrikam uses to submit a 3A2 PIP request to Contoso. The LOBWebApplication project is installed in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK. To run the Web application, you have to create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) virtual directory and build the LOBWebApplication project.  
  
> [!NOTE]
>  If you completed the DoubleAction tutorial, you do not need to perform this step.  
  
### To create the LOBWebApplication virtual directory  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services Manager**.  
  
    > [!NOTE]
    >  If you have already done the Double Action tutorial, you will already have created the LOBWebApplication virtual directory for that tutorial. If so, you do not have to perform these steps. You will, however, have to change the permissions for the virtual directory from **Run scripts** to **Read**.  
  
2.  In Internet Information Services Manager, expand **<computer_name> (local computer)**, and then expand **Web Sites**.  
  
3.  Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.  
  
4.  On the **Welcometo the Virtual Directory Creation Wizard page**, click **Next**.  
  
5.  On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.  
  
6.  On the **Web Site Content Directory** page, click **Browse**, select the **\<drive>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBWebApplication** folder, and then click **OK**. Click **Next**.  
  
7.  On the **Virtual Directory Access Permissions** page, click **Next**.  
  
8.  Click **Finish** to create the virtual directory.  
  
### Excluding LOBWebApplication from SharePoint  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  
  
    > [!NOTE]
    >  If you have already done the Double Action tutorial, you will already have excluded the LOBWebApplication virtual directory from SharePoint for that tutorial. If so, you do not have to perform these steps.  
  
2.  On the **Central Administration** page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.  
  
3.  If you do not see the URL configured on the computer, click **Complete list**.  
  
4.  Select **Default Web Site**.  
  
5.  In the **Virtual Server Management** section, click **Define managed paths**.  
  
6.  In the **Add New Path** section, in the **Path** box, type "/LOBWebApplication". For **Type**, select **Excluded Path**, and then click **OK**.  
  
### To build the LOBWebApplication project  
  
1.  Start **Microsoft Visual Studio 2012**.  
  
2.  From the **File** menu, point to **Open**, and then click **Project\Solution**.  
  
3.  In the Open Project dialog box, in **Look In**, move to **\<drive>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\ SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution, and then click **Open**.  
  
4.  In Solution Explorer, right-click the top node (http://localhost/LOBWebApplication), and then click **Add Reference**.  
  
5.  In the Add Reference dialog box, click **Browse** and move to **\<drive>:\Program Files\Microsoft  BizTalk \<version> Accelerator for RosettaNet\bin**.  
  
6.  **Select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll** assemblies **and then click OK.**  
  
7.  On the **Build** menu, click **Build Web Site**.  
  
### To run the LOBWebApplication project  
  
1.  In Solution Explorer, right-click **default.aspx**, and then select **Set As Start Page**.  
  
2.  On the **Debug** menu, click **Start Without Debugging**.  
  
## See Also  
 [Testing the Solution](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)