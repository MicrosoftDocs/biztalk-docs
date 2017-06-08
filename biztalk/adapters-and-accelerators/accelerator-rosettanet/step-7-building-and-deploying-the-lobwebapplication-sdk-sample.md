---
title: "Step 7: Building and Deploying the LOBWebApplication SDK Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, building solutions"
  - "double action tutorial, deploying solutions"
ms.assetid: f61de666-ebda-4831-9669-598e9284e4c1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Building and Deploying the LOBWebApplication SDK Sample
In this step, you create the line-of-business (LOB) application that Fabrikam uses to submit Partner Interface Process (PIP) requests to Contoso. You can find the LOBWebApplication project in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK folder. To run the Web application, you have to create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) virtual directory, and then build the LOBWebApplication project.  
  
### To create the LOBWebApplication virtual directory  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In the Internet Information Services Manager window, expand **<computer_name> (local computer)**, and then expand **Web Sites**.  
  
3.  Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.  
  
4.  On the **Welcometo the Virtual Directory Creation Wizard** page, click **Next**.  
  
5.  On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.  
  
6.  On the **Web Site Content Directory** page, click **Browse**. In the Browse For Folder dialog box, move to ***\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBWebApplication**, and then click **OK**. Click **Next**.  
  
7.  On the **Virtual Directory Access Permissions** page, deselect **Read**, select **Run scripts (such as ASP)**, and then click **Next**.  
  
8.  On the **You have successfully completed the Virtual Directory Creation Wizard** page, click **Finish** to create the virtual directory.  
  
### To exclude the LOBWebApplication Web site from the SharePoint configuration  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  
  
2.  On the **Central Administration** Web page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.  
  
3.  If you do not see the URL configured on the computer, click **Complete list**.  
  
4.  On the **Virtual Server List** page, select **Default Web Site**.  
  
5.  In the **Virtual Server Management** section, click **Define managed paths**.  
  
6.  In the **Add New Path** section, in the **Path** box, type **/LOBWebApplication**.  
  
7.  For **Type**, select **Excluded Path**, and then click **OK**.  
  
### To build the LOBWebApplication project  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2008**, and then click **Microsoft Visual Studio 2008**.  
  
2.  On the **File** menu, point to **Open**, and then click **Project/Solution**.  
  
3.  In the Open Project dialog box, move to ***\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution file, and then click **Open**.  
  
4.  In Solution Explorer, right-click **http://localhost/LOBWebApplication**, and then click **Add Reference**.  
  
5.  In the Add Reference dialog box, click **Browse**. In the Add Reference dialog box, move to ***\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\Bin** folder.  
  
6.  From the Bin folder, select the **Microsoft.Solutions.BTARN.ConfigurationManager.dll** and **Microsoft.Solutions.BTARN.Shared.dll** assemblies, and then click **Open.**  
  
7.  Click **OK** to close the **Add Reference** dialog box.  
  
8.  In Solution Explorer, right-click **Solution 'LOBWebApplication'** and then click **Build Solution**.  
  
9. Right-click **default.aspx**, and then click **Set as Start Page**.  
  
## See Also  
 [Testing the Double Action Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)