---
title: "Generating and Publishing MT-MX Forms on the SharePoint Site | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generating and Publishing MT/MX Forms on the SharePoint Site
**To generate and publish MT/MX forms on a SharePoint site:**  

1. Download the Form Generator Utility and save it locally on the computer.  

2. Open the **FormGenerator.sln** from the folder downloaded above and compile the solution.  

3. At a command prompt, access the folder of compiled executable (FormGenerator.exe). For example, if you have built the utility in debug mode, access the **..\bin\debug** folder.  

4. Type FormGenerator.exe [-b] [-\<No. of Template folder paths\>]  

    `<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`. Replace the parameters with the newly-created folder names.  

5. The above command will also generate the Envelope schema needed for MX message repair.  

6. Go to output folder \<DestinationFolderPath\>. In \<DestinationFolderPath\>, open the folder of the InfoPath form template for which you want to generate the form. For example, if you want to generate the MT103 InfoPath form, then open the MT103 folder at the DestinationFolderPath and open the TemplateDS.sln.  

7. In the Solution Explorer, double click the **manifest.xsf**. It will open the design file of the InfoPath form which will take some time to get opened.  

   > [!NOTE]
   >  The MX messages manifest.xsf might take 2-5 minutes to get opened.  

8. In the manifest.xsf, go to **Tools ->Form Options-> Security and Trust** menu option. Check the **Full Trust** option must be enabled for the permission.  

9. Select the **Sign this form Template** checkbox. Click **Select certificate**. In this, select the certificate with which you want to sign the form. Click **OK**.  

10. Save **manifest.xsf**.  

11. Go to **View -> Design Tasks**. On the Design Tasks pane, click **Publish Form Template** option.  

12. In the publishing wizard window, select **To a network location** and click **Next**.  

13. In the Form template path and file name textbox, type <strong>http://localhost/sites/BASSite/Templates/\<MessageType\>.xsn</strong> and type **\<MessageType\>** in the Form Template name textbox and click **Next**.  

14. Click **Next**.  

15. Click **Publish and close**.  

16. In the Internet Explorer, open your SharePoint site **http://localhost/sites/bassite/templates**.  

17. Point to **\<MessageType\>**, click the down arrow next to it, and then click **Edit Properties**.  

18. In the Templates:\< MessageType\> window, in the Namespace box:  

    - If you are generating MT InfoPath forms, type: **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**  

    - If you are generating MX InfoPath forms, type: <strong>http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageName\></strong>  

       This will help in identifying the message instance with the corresponding template.  

19. Click **Save and Close**.
