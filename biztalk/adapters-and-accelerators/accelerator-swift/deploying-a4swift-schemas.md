---
title: "Deploying A4SWIFT Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, A4SWIFT"
  - "deploying, A4SWIFT schemas"
  - "A4SWIFT, deploying schemas"
  - "schemas, deploying"
ms.assetid: a6aed2cd-3578-442e-ab1e-8284cc5f7b72
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying A4SWIFT Schemas
You must deploy schemas for the SWIFT messages that you want to exchange.  
  
 **Summary**  
  
 Deploy the following schemas:  
  
-   SWIFT Base Types.xsd  
  
-   SWIFT Common Data Types.xsd  
  
-   Specific schema for a message type, for example, MT103.xsd  
  
### To create a strong-named SWIFT project  
  
1. In Visual Studio, click **File**, point to **New**, and then click **Project**.  
  
2. In the New Project dialog box, in the **Project types** pane, select the **BizTalk Projects** folder.  
  
3. In the **Templates** pane, select **Empty BizTalk Server Project**.  
  
4. In the **Name** box, type the name you want for the project name.  
  
5. In the **Solution** box, select **Create new Solution**. In the **Location** box, enter the location of the project that you are adding the schema project to.  
  
6. Click **OK** to open the new project.  
   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] adds a new project to Solution Explorer, and creates the project folder and files in the folder specified.  
  
7. Start Visual Studio command prompt.  
  
8. At the Visual Studio command prompt, browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT**.  
  
9. At the command prompt, type **sn –k key.snk**, and then press ENTER. Ensure that a message is displayed in the command-prompt window indicating that a key pair was written to key.snk.  
  
10. In Solution Explorer, right-click your project name, and then click **Properties**.  
  
11. In the left pane of the **Property Pages** dialog box, click **Assembly**.  
  
12. In the right pane of the **Property Pages** dialog box, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis () button.  
  
13. In the **Assembly Key File** dialog box, browse to **\<*drive*\>:\Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)], click **key.snk**, and then click **Open**.  
  
14. In the **Property Pages** dialog box, click **OK** to save your changes.  
  
### To add a SWIFT schema  
  
1.  In Solution Explorer of Visual Studio, open your project.  
  
2.  Right-click your project, point to **Add**, and then click **Existing Item**.  
  
3.  In the **Add Existing Item** dialog box, in the :\\**Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Schemas**. Select the **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** schemas, and then click **Add**.  
  
4.  Right-click your project, point to **Add**, and then click **Add Existing Item**.  
  
5.  In the **Add Existing Item** dialog box, in the **Look in** drop-down box, move to **\<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category n\MTxxx**. Select a schema for a message type, for instance **MT103.xsd**, and then click **Add**.  
  
    > [!NOTE]
    >  A4SWIFT adds the schema for your project, as shown in Solution Explorer.  
  
6.  In Solution Explorer, right-click the project name, and then click **Build**.  
  
7.  In Solution Explorer, right-click the project name, and then click **Deploy**.