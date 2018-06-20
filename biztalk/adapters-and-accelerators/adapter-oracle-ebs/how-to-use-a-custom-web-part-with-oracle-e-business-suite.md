---
title: "How to use a custom web part with Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf420061-41d1-4d97-9be1-403cd101e41c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to use a custom web part with Oracle E-Business Suite
This section provides information about using a custom Web Part with Microsoft Office SharePoint Server. To use a custom Web Part, you must do the following:  
  
1.  Create a custom Web Part  
  
2.  Deploy the custom Web Part to a SharePoint portal  
  
3.  Configure the SharePoint portal to use the custom Web Part  
  
## Before You Begin  
 Before you create a custom Web Part:  
  
-   Publish the Oracle E-Business Suite artifacts as a  WCF service. For more information, see [Step 1: Use the Oracle E-Business Adapter to create and publish a WCF service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
-   Create an application definition file for the Oracle E-Business Suite artifacts using the Business Data Catalog in Microsoft Office SharePoint Server. For more information, see [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
##  <a name="Create_a_Custom_Web_Part"></a> Step 1: Create a custom Web Part  
  
1.  Start Visual Studio, and then create a project.  
  
2.  In the **New Project** dialog box, from the **Project types** pane, select **Visual C#**. From the **Templates** pane, select **Class Library**.  
  
3.  Specify a name and location for the solution. For this topic, specify `CustomWebPart` in the **Name** and **Solution Name** boxes. Specify a location, and then click **OK**.  
  
4.  Add a reference to the System.Web component into the project. Right-click the project name in **Solution Explorer**, and then click **Add Reference**. In the **Add Reference** dialog box, select **System.Web** in the **.NET** tab, and then click **OK**. The System.Web component contains the required namespace of System.Web.UI.WebControls.WebParts.  
  
5.  Add the required code based on your issue in the project. For the code sample that is relevant to a certain issue, see “Issues Involving Custom Web Parts” in [Considerations using the Oracle-Business Suite adapter with SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/considerations-using-the-oracle-business-suite-adapter-with-sharepoint.md).  
  
6.  Build the project. On successful build of the project, a .dll file, CustomWebPart.dll, will be generated in the \<project folder\>/bin/Debug folder.  
  
7.  **Only for 64-bit computer**: Sign the CustomWebPart.dll file with a strong name before performing the following steps. Otherwise, you will not be able to import, and hence use the CustomWebPart.dll in the SharePoint portal in “Step 3: Configure the SharePoint Portal to use the custom Web Part.” For information about how to sign an assembly with a strong name, see [How to: Sign an Assembly with a Strong Name](https://msdn.microsoft.com/library/xc31ft41.aspx).
  
## Step 2: Deploy the custom Web Part to a SharePoint Portal  
 You must do the following to make the CustomWebPart.dll file (custom Web Part) that is created in “Step 1: Create a custom Web Part” of this topic usable on the SharePoint portal:  
  
- **Copy the CustomWebPart.dll file to the bin folder of the SharePoint Portal**: Microsoft Office SharePoint Server creates portals under the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories folder. A folder is created for each portal, and can be identified with the port number. You must copy the CustomWebPart.dll file created in “Step 1: Create a custom Web Part” of this topic to the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number\>\bin folder. For example, if the port number of your SharePoint portal is 13614, you must copy the CustomWebPart.dll file to the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\13614\bin folder.  
  
  > [!TIP]
  >  Another way to find the folder location of your SharePoint portal is by using the **Internet Information Services (IIS) Manager** window (**Start** > **Run** > **inetmgr**). Locate your SharePoint portal in the **Internet Information Services (IIS) Manager** window ([computer_name] > Web Sites > [Portal-Name]), right-click, and then click **Properties** in the shortcut menu. In the properties dialog box of the SharePoint portal, click the **Home Directory** tab, and then select the **Local path** box.  
  
- **Add the Safe Control Entry in the web.config File**: Because the CustomWebPart.dll file will be used on different computers and by multiple users, you must declare the file as “safe.” To do so, open the web.config file located in the SharePoint portal folder at \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number\>. Under the `<SafeControls>` section of the web.config file, add the following safe control entry:  
  
  - **On 32-bit computer:**  
  
    ```  
    <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
  - **On 64-bit computer:**  
  
    ```  
    <SafeControl Assembly="CustomWebPart, Version=1.0.0.0, Culture=neutral, PublicKeyToken=<PUBLICKKEYTOKEN_OF_CustomWebPart.dll>" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
    Save the web.config file, and then close it.  
  
## Step 3: Configure the SharePoint portal to use the custom Web Part  
 You need to add the custom Web Part to the Microsoft Office SharePoint Server Web Part Gallery, so that you can use it on your SharePoint portal. To do so:  
  
1. Start SharePoint 3.0 Central Administration. Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.  
  
2. In the left navigation pane, click the name of the Shared Service Provider (SSP) to which you want to add the custom Web Part.  
  
3. On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.  
  
4. On the Site Settings page, click **Web Parts** under the **Galleries** column.  
  
5. On the Web Part Gallery page, to add the custom Web Part to the gallery,  click **New**. At this point the custom Web Part is not available in the Web Part Gallery page.  
  
6. On the New Web Parts page, locate **CustomWebPart** (name of the custom Web Part) in the list, select the check box on the left, and then click **Populate Gallery** on the top of the page. This will add the **CustomWebPart** entry in the Web Part Gallery page.  
  
   Now you can use the custom Web Part (**CustomWebPart**) to create Web Parts in your SharePoint portal. The custom Web Part (**CustomWebPart**) will appear under the **Miscellaneous** section in the Add Web Parts page.  
  
## See Also  
[Use the Oracle E-Business Suite adapter with SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)