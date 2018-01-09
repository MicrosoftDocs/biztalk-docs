---
title: "How to Use the Mapping Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0379f3dc-415b-43d6-917e-b2891d185ffe
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Use the Mapping Wizard
This version of Enterprise Single Sign-On includes the Mapping Wizard, which allows you to easily create mappings for affiliate applications.  
  
> [!NOTE]
>  You can only use the Mapping Wizard if the External UserID is based on the Windows domain account.  
  
### To start the Mapping Wizard  
  
1.  Open Enterprise Single Sign-On.  
  
2.  In the scope pane, click **Affiliate Applications**.  
  
3.  Right click the appropriate affiliate application.  
  
4.  Click **Create Mappings**.  
  
     The Mapping Wizard appears.  
  
### To use the Mapping Wizard  
  
1.  **Welcome to the Mapping Wizard**  
  
    -   Verify that this is the correct affiliate application, and click **Next**.  
  
2.  **Mappings File Option** page  
  
    -   ENTSSO manages mappings through an XML file. You can choose to create a new file or use an existing one.  
  
3.  **Files Location** page  
  
    -   Select the files to be used.  
  
    -   You must click **Validate** to validate the files before proceeding. The validation status appears in the **Status** window.  
  
4.  **Accounts** page  
  
    -   Choose one or more accounts to generate the new mappings file, and click **Validate**.  
  
5.  **External User Name** page  
  
    -   Define how the external user name is generated from the Windows user account. As you make selections in the boxes, you can see how the names will appear in the **Example** box.  
  
6.  **Generate** page  
  
    -   Click **Start** to generate the mappings file. (You will have an opportunity on the next page to view or edit the file as necessary before mappings are created.) Results are displayed in the three windows below.  
  
    -   The **Number** of mappings in selected accounts is an approximation, because accounts may be nested in other accounts.  
  
    -   Click **View Log File** to examine any errors or warnings that might have occurred.  
  
7.  **Options** page  
  
    -   Your file has been created. Click **View/Edit Mappings File** if desired.  
  
    -   Click **Enable mappings** if you want the mappings to be automatically enabled. (If you do not click this, you will have to enable them manually.)  
  
    -   Click **Set Password** to automatically set the password for these mappings.  
  
8.  **Create** page  
  
    -   Before creating the mappings, click **View Mappings File** if desired.  
  
    -   When you are ready, click **Start** to perform the mapping operation. Your status is displayed in the three boxes below.  
  
    -   Click **View Log File** to examine any errors or warnings that might have occurred.  
  
9. **Completing the Mapping Wizard screen**  
  
    -   Select any options desired, and then click **Finish**.  
  
## See Also  
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)   
 [SSO Security Recommendations](../esso/sso-security-recommendations.md)