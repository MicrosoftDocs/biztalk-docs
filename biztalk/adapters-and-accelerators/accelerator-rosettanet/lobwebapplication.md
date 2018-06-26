---
title: "LOBWebApplication | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows SharePoint Services, LOBWebApplication"
  - "ASPX pages, LOBWebApplication utility"
  - "virtual servers"
  - "ASPX pages, submitting actions"
  - "LOBWebApplication"
  - "ASPX pages, response messages"
  - "LOBWebApplication utility"
ms.assetid: 2d578efd-72a9-4621-9274-30792bf94b6c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# LOBWebApplication
You use the LOBWebApplication utility to submit an action or response message from an ASPX page to a trading partner, simulating an actual line-of-business Web application.  
  
 After you have set up the ASPX page, you start the page, and enter the parameters for a message: the home and partner organizations; the PIP code, version, and instance ID; and the message category. You can then modify the service content, and submit the message.  
  
## Location in SDK  
 \<*drive*\>\Program Files (86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication  
  
## Adding a Virtual Server for LOBWebApplication  
  
#### To add a virtual server  
  
1.  Click **Start**, point to **AllPrograms**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In Information Services Manager, expand **\<Computer name\> (local computer)**, expand **Web Sites**, and then right-click **Default Web Site**.  
  
3.  Point to **New**, and then click **Virtual Directory**.  
  
4.  On the **Virtual Directory Creation Wizard** page, click **Next**, and then type an alias for the site, such as **LOBWebApplication**.  
  
5.  On the **Web Site Content Directory** page, click **Browse**, move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication, click **OK**, and then click **Next**.  
  
6.  On the **Virtual Directory Access Permissions** page, select **Read** and **Run scripts**, and then click **Next**. Click **Finish**.  
  
7.  Add the service account user that was used to configure BTARN, for example, hostsvc, to the STS_WPG.  
  
8.  Delete all files from C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files. You may have to run the iisreset program to unlock the files before you can delete them.  
  
9. In IIS Manager, set the LOBWebApplication to run under the Application Pool BTARNHTTPReceivePool.  
  
10. In IIS Manager, in the Directory Security Properties section for the LOBWebApplication utility, disable the option for the virtual directory to run as anonymous.  
  
## Building LOBWebApplication  
  
#### To build LOBWebApplication  
  
1. Start Visual Studio.  
  
2. On the **File**, point to **Open**, and then click **Open Solution**.  
  
3. Move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication, select **LOBWebApplication.sln**, and then click **Open**.  
  
   > [!NOTE]
   >  If you have not added a virtual server for LOBWebApplication, the solution will not open correctly in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
4. Right-click **References**, and then click **Add Reference**.  
  
5. In the **Add Reference** dialog box, click **Browse**, move to \<*drive*\>:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin, select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll files, and then click **Open**.  
  
6. Right-click **LOBWebApplication**, and then click **Build**.  
  
## Running LOBWebApplication  
  
#### To run LOBWebApplication and submit a message  
  
1.  Click **Start**, point to **All Programs**, and then click **Internet Explorer**.  
  
2.  In Internet Explorer, in the **Address** box, type http://localhost/LOBWebApplication, and then click **Go**.  
  
3.  In the **Submit Message** dialog box, type the home organization, the partner organization, the PIP code, the PIP version, the PIP Instance ID, and the message category.  
  
4.  Modify the service content as needed.  
  
5.  Click **Submit**.  
  
## Remarks  
 The LOBWebApplication utility generates an instance of the message from the specified PIP, and enters service content from the generated message instance into the ASPX page. To do this, the utility uses the same technique that it uses to generate a well-formed message instance directly from a PIP. For more information, see [Creating a Well-Formed Message Instance from a PIP](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md). You can populate any field of the service content in the ASPX page with actual data to generate an actual message instance.  
  
 You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message. You use the LOBApplication utility to simulate a line-of-business desktop application submitting a message.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)
