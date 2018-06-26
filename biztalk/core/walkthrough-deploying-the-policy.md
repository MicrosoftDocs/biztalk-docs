---
title: "Walkthrough: Deploying the Policy | Microsoft Docs"
ms.custom: ""
ms.date: "2016-04-05"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 205760e2-9cd4-496f-93cd-0f93bc5d3231
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Deploying the Policy
This walkthrough provides step-by-step instructions for deploying the **ProcessPurchaseOrder** policy in the following three ways:  
  
-   Exporting and importing the policy by using the Business Rules Engine Deployment Wizard.  
  
-   Exporting the policy to an XML file and importing the policy from an XML file by using the BizTalk Server Administration console.  
  
-   Exporting the policy as part of an MSI file and importing the MSI file by using BizTalk Server Administration console.  
  
## Prerequisites  
 You must complete the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough before performing this walkthrough.  
  
## Overview of This Walkthrough  
 This topic  contains the following three walkthroughs:  
  
1.  The first walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using the Business Rules Engine Deployment Wizard. The following table describes the procedures in this walkthrough.  
  
    |Procedure title|Procedure description|  
    |---------------------|---------------------------|  
    |To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard|Provides step-by-step instructions for exporting versions 1.0 and 1.1 of the **POVocabulary** vocabulary to XML files by using the Business Rules Engine Deployment Wizard.|  
    |To export ProcessPurchaseOrder 1.3 by using the Business Rules Engine Deployment Wizard|Provides step-by-step instructions for exporting version 1.3 of the **ProcessPurchaseOrder** policy to an XML file by using the Business Rules Engine Deployment Wizard.|  
    |To delete ProcessPurchaseOrder and POVocabulary|Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary so that you can test importing the XML files to re-create them.|  
    |To import from XML to re-create POVocabulary 1.0 and 1.1|Provides step-by-step instructions for importing the vocabulary XML file you created in the first procedure to re-create the **POVocabulary** vocabulary.|  
    |To verify that POVocabulary 1.0 and 1.1 are re-created|Provides step-by-step instructions for using the Business Rule Composer to verify that versions 1.0 and 1.1 of **POVocabulary** are re-created.|  
    |To import from XML to re-create ProcessPurchaseOrder 1.3|Provides step-by-step instructions for importing the policy XML file you created in the second procedure to re-create version 1.3 of the **ProcessPurchaseOrder** policy.|  
    |To verify that ProcessPurchaseOrder 1.3 is re-created|Provides step-by-step instructions for using the Business Rule Composer to verify that version 1.3 of the **ProcessPurchaseOrder** policy is re-created.|  
  
2.  The second walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an XML file exported from the BizTalk Server Administration console The following table describes the procedures in this walkthrough.  
  
    |Procedure title|Procedure description|  
    |---------------------|---------------------------|  
    |To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file|Provides step-by-step instructions for using the BizTalk Server Administration console to export the **ProcessPurchaseOrder** policy and the **POVocabulary** vocabulary to an XML file.|  
    |To delete the ProcessPurchaseOrder policy|Provides step-by-step instructions for deleting the **ProcessPurchaseOrder** policy from **RuleTestApp** and the rule engine database.|  
    |To import the XML file to re-create the ProcessPurchaseOrder policy|Provides step-by-step instructions for importing the XML file you exported in the first procedure to re-create the **ProcessPurchaseOrder** policy.|  
    |To add the ProcessPurchaseOrder policy to the RuleTestApp application|Provides step-by-step instructions for adding the **ProcessPurchaseOrder** policy to the **RuleTestApp** application.|  
  
3.  The third walkthrough contains procedures for deploying the **ProcessPurchaseOrder** policy by using an MSI file exported from the BizTalk Server Administration console. The following table describes the procedures in this walkthrough.  
  
    |Procedure title|Procedure has step-by-step instructions for|  
    |---------------------|---------------------------------------------------|  
    |To export the RuleTestApp application to an MSI file|Provides step-by-step instructions for exporting the **RuleTestApp** application to an MSI file, which is used later to re-create the application.|  
    |To delete the RuleTestApp application|Provides step-by-step instructions for deleting the **RuleTestApp** application so that you can test re-creating the application by using the MSI file.|  
    |To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted|Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and POVocabulary vocabulary are deleted.|  
    |To import the MSI file to re-create the RuleTestApp application|Provides step-by-step instructions for using the BizTalk Server Administration console to import the MSI file to re-create the **RuleTestApp** application.|  
    |To verify that the ProcessPurchaseOrder policy is added to RuleTestApp|Provides step-by-step instructions for using the BizTalk Server Administration console to verify that the **ProcessPurchaseOrder** policy is added to the **RuleTestApp** application.|  
    |To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created|Provides step-by-step instructions for using the Business Rule Composer to verify that the **ProcessPurchaseOrder** policy and **POVocabulary** vocabulary are re-created.|  
    |To test the solution|Provides step-by-step instructions for testing the solution.|  
  
## Procedures for Deploying the ProcessPurchaseOrder Policy by Using the Business Rules Engine Deployment Wizard  
  
#### To export POVocabulary 1.0 and 1.1 by using the Business Rules Engine Deployment Wizard  
  
1.  On the **Start** menu, open **Business Rules Engine Deployment Wizard**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  Click **Next**.  
  
3.  On the **Deployment Task** page, select **Export Policy/Vocabulary to file from database**, and then click **Next**.  
  
4.  On the **Policy Store** page, click **Next**.  
  
5.  On the **Export Policy/Vocabulary** page, click **Vocabulary**.  
  
6.  Select **POVocabulary.1.0** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary10.xml**, and then click **Next**.  
  
7.  On the **Ready** page, click **Next**.  
  
8.  On the **Exporting Policy/Vocabulary** page, click **Next.**  
  
9. Select **Run this wizard again**, and then click **Finish**.  
  
     Because you selected **Run this wizard again**, the first screen of the wizard appears again.  
  
10. Repeat steps 2-6.  
  
11. Select **POVocabulary.1.1** from the drop-down list for **Policy/Vocabulary**, type or browse to specify the XML output file name as **C:\BRE-walkthroughs\POVocabulary11.xml**, and then click **Next**.  
  
12. Repeat steps 8 and 9.  
  
13. Click **Finish**.  
  
    > [!NOTE]
    >  You need to export both version 1.0 and version 1.1 of **POVocabulary** because **ProcessPurchaseOrder** 1.3 depends on both versions of **POVocabulary**. The **Maximum number of items allowed** definition is used from version 1.1 of the vocabulary. The **Requested Quantity** and **Request Status** definitions are used from version 1.0.  
  
#### To export ProcessPurchaseOrder 1.3 by using the Business Rule Engine Deployment Wizard  
  
1.  On the **Start** menu, open **Business Rules Engine Deployment Wizard**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  On the **Welcome to the Rules Engine Deployment Wizard** page, click **Next**.  
  
3.  Select **Export Policy/Vocabulary to file from database**, and then click **Next**.  
  
4.  On the **Policy Store** page, click **Next**.  
  
5.  Verify that the **Policy** option is selected.  
  
6.  Select **ProcessPurchaseOrder.1.3** from the drop-down list for **Policy/Vocabulary**.  
  
7.  Type or browse to specify **C:\BRE-walkthroughs\ProcessPOPolicy13.xml** as the XML output file name.  
  
8.  Click **Next** thrice, and then click **Finish**.  
  
#### To delete ProcessPurchaseOrder and POVocabulary  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Delete**. If **Delete** is disabled, right-click **Version 1.0**, and then click **Undeploy**.  
  
    > [!NOTE]
    >  The deployed policy versions cannot be deleted. You must undeploy a policy before deleting a policy version.  
  
3.  Click **Yes** in the confirmation message box.  
  
4.  Repeat steps 2 and 3 to delete **Version 1.1**.  
  
5.  Repeat steps 2 and 3 to delete **Version 1.2**.  
  
6.  Right-click **Version 1.3 - Deployed**, and then click **Undeploy**. If the **Undeploy** option is disabled, ignore this step.  
  
7.  In the Facts Explorer window, expand **Vocabularies**, right-click **POVocabulary**, and then click **Delete**.  
  
#### To import from XML to re-create POVocabulary 1.0 and 1.1  
  
1.  On the **Start** menu, open **Business Rules Engine Deployment Wizard**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.  
  
3.  On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.  
  
4.  On the **Policy Store** page, click **Next**.  
  
5.  Browse and select the **POVocabulary10.xml** file you created in the first procedure.  
  
6.  Click **Open** or double-click **POVocabulary10.xml**.  
  
7.  Click **Next** in the Business Rules Engine Deployment Wizard.  
  
8.  Click **Next**.  
  
9. Click **Next**.  
  
10. Select **Run this wizard again**, and then click **Finish**.  
  
11. Repeat steps 2-9 to import **POVocabulary11.xml**.  
  
12. Click **Finish**.  
  
#### To verify that POVocabulary 1.0 and 1.1 are re-created  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Facts Explorer window, click the **Vocabularies** tab.  
  
3.  Expand **Vocabularies**, and you should see **POVocabulary**.  
  
4.  Expand **POVocabulary**, and you should see **Version 1.0** and **Version 1.1**.  
  
#### To import from XML to re-create ProcessPurchaseOrder 1.3  
  
1.  On the **Start** menu, open **Business Rules Engine Deployment Wizard**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  On the **Welcome to the Rules Engine Deployment Wizard**, click **Next**.  
  
3.  On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from fileto database from file**, and then click **Next**.  
  
4.  On the **Policy Store** page, click **Next**.  
  
5.  Browse and select the **ProcessPOPolicy13.xml** file you created earlier in this walkthrough.  
  
6.  Click **Open** or double-click **ProcessPOPolicy13.xml**.  
  
7.  Click **Next** in the Business Rules Engine Deployment Wizard.  
  
8.  Click **Next**.  
  
9. Click **Next**, and then click **Finish**.  
  
#### To verify that ProcessPurchaseOrder 1.3 is re-created  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have it already open, press F5 or click **Reload** on the **File** menu to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Policy Explorer window, expand **Policies** and you should see **ProcessPurchaseOrder**.  
  
3.  Expand **ProcessPurchaseOrder** and you should see **Version 1.3 - Published**.  
  
## Procedures for Deploying the Policy by Using an XML file Exported from the BizTalk Server Administration Console  
  
#### To export the ProcessPurchaseOrder 1.3 policy and the POVocabulary vocabulary to an XML file  
  
1. On the **Start** menu, open [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]. If you have the tool already open, press F5 to refresh it.  
  
2. Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand **RuleTestApp**.  
  
3. Click **Policies** and make sure that you see the ProcessPurchaseOrder 1.3 policy in the list.  
  
4. Right-click **ProcessPurchaseOrder**, and then click **Export**.  
  
5. In the **Export Policies** dialog box, make sure the **ProcessPurchaseOrder** policy and the **POVocabulary** are selected.  
  
   > [!NOTE]
   >  You can export all the policies in an application to an XML file by right-clicking **RuleTest** and then clicking **Export** on the **Policies** menu. This way you can export all the policies and vocabulary used by this application to a single XML file.  
  
   > [!NOTE]
   >  You can export all the policies in all the applications to an XML file by right-clicking the **Applications** node and then clicking **Export** on the **Policies** menu. This way you can export all the policies and vocabularies used by all the applications into a single XML file.  
  
6. Specify an output XML file name (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**), and then click **Ok**.  
  
#### To delete the ProcessPurchaseOrder policy  
  
1.  In BizTalk Server Administration, right-click **ProcessPurchaseOrder** in the list, and then click **Remove**.  
  
2.  Click **Yes** in the **Remove Policy** message box.  
  
    > [!NOTE]
    >  If the policy is in the deployed state, it cannot be removed. Right-click **ProcessPurchaseOrder**, and then click **Undeploy** to undeploy the policy. The **Remove** menu item is available when the policy is undeployed.  
  
    > [!NOTE]
    >  The vocabularies on which the **ProcessPurchaseOrder** policy depends, in this case **POVocabulary**, are also deleted.  
  
    > [!NOTE]
    >  When you remove a policy from an application, the policy and the vocabularies that it depends on are deleted from the rule engine database as well, not just from the application.  
  
#### To import the XML file to re-create the ProcessPurchaseOrder policy  
  
1. In BizTalk Server Administration, expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.  
  
2. Right-click **Applications**, point to **Import**, and then click **Policies**.  
  
3. Browse, and double-click the XML file (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) that you created in the first procedure.  
  
4. Expand **\<All Artifacts\>** under **Applications**.  
  
5. Click **Policies**, and you should see version 1.3 of the **ProcessPurchaseOrder** policy in the list.  
  
6. Press F5 to refresh the view. The **ProcessPurchaseOrder** policy should be in the **Not Published** state.  
  
#### To add the ProcessPurchaseOrder policy to the RuleTestApp application  
  
1.  In BizTalk Server Administration, right-click **ProcessPurchaseOrder** policy, and then click **Publish**.  
  
    > [!NOTE]
    >  Only published policies can be added to a BizTalk application.  
  
2.  In the **Applications** node, expand **RuleTestApp**.  
  
3.  Click **Policies** in **RuleTestApp**.  
  
4.  Right-click in the list on the right, point to **Add**, and then click **Policy**.  
  
5.  Expand the **ProcessPurchaseOrder** node, select the check box for **Version 1.3 (Published)**, and then click **OK**. .  
  
6.  Right-click **ProcessPurchaseOrder**, and then click **Deploy**. If you do not see **ProcessPurchaseOrder** in the list, press F5 to refresh the view.  
  
7.  Click **Yes** in the confirmation message box.  
  
## Procedures for Deploying the Policy by Using an MSI File  
  
#### To export the RuleTestApp application to an MSI file  
  
1. On the **Start** menu, open **BizTalk Server Administration**. If you have the tool already open, press F5 to refresh it.  
  
2. Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.  
  
3. Right-click **RuleTestApp**, point to **Export**, and then click **MSI file**.  
  
4. On the **Welcome to the Export MSI File Wizard** page, click **Next**.  
  
5. On the **Select Resources** page, review all the default options, and then click **Next**.  
  
6. On the **Specify IIS Hosts** page, click **Next**.  
  
7. On the **Dependencies** page, click **Next**.  
  
8. On the **Destination** page, specify the directory and name for the MSI as **C:\BRE-Walkthroughs\RuleTestApp.msi**.  
  
9. Click **Export**.  
  
10. On the **Summary** page, click **Finish**.  
  
    > [!NOTE]
    >  When you export the RuleTestApp application, the policies and vocabularies used by the application are also exported in the MSI file. Later, when you import the MSI file, the vocabulary, policy, and application are all re-created.  
  
#### To delete the RuleTestApp application  
  
1.  In BizTalk Server Administration, right-click **RuleTestApp**, and check if the **Delete** menu is enabled or disabled.  
  
2.  If **Delete** is disabled, right-click **RuleTestApp**, click **Stop**, select **Full Stop - Terminate Instance**, and then click **Stop**.  
  
3.  Right-click **RuleTestApp**, and then click **Delete**.  
  
4.  Click **Yes** to confirm deletion.  
  
    > [!NOTE]
    >  When you delete an application, all the policies in the application and dependent vocabularies are deleted from the rule engine database as well.  
  
#### To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are deleted  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have Business Rule Composer already open, press F5 to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Policy Explorer window, expand **Policies**, and make sure that the ProcessPurchaseOrder policy does not exist.  
  
3.  In the Facts Explorer window, expand **Vocabularies**, and make sure that POVocabulary does not exist.  
  
#### To import the MSI file to re-create the RuleTestApp application  
  
1. On the **Start** menu, open **BizTalk Server Administration**. If you have the BizTalk Server Administration console already open, press F5 to refresh it.  
  
2. Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.  
  
3. Right-click **Applications**, point to **Import**, and then click **MSI file**.  
  
4. On the **Welcome to the Import Wizard** page, browse and select the MSI file (RuleTestApp.msi) you exported earlier for the **MSI file to import** setting.  
  
5. Click **Next**.  
  
6. On the **Application Settings** page, click **Next**.  
  
7. On the **Application Target Environment Settings** page, click **Next**.  
  
8. On the **Import Summary** page, click **Import**.  
  
9. On the **Import Succeeded** page, click **Finish**. You should see that the **RuleTestApp** application is created under **Applications** in the BizTalk Server Administration console.  
  
#### To verify that the ProcessPurchaseOrder policy is added to RuleTestApp  
  
1.  Expand **RuleTestApp** in the BizTalk Server Administration console.  
  
2.  Select **Policies** and you should see **ProcessPurchaseOrder** in the list in the right pane.  
  
#### To verify that the ProcessPurchaseOrder policy and POVocabulary vocabulary are re-created  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have it already open, press F5 to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Policy Explorer window, expand **Policies**, and make sure that **ProcessPurchaseOrder** exists.  
  
3.  In the Facts Explorer window, expand **Vocabularies**, and make sure that **POVocabulary** exists.  
  
#### To test the solution  
  
1. On the **Start** menu, open **BizTalk Server Administration**. If you have the BizTalk Server Administration console already open, press F5 to refresh it.  
  
2. Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.  
  
3. Right-click **RuleTestApp**, and then click **Start**.  
  
4. Click **Start**.  
  
5. Copy **SamplePO.xml** that you created in [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) to the input directory for the orchestration.  
  
6. You should see an output file in the output directory for the orchestration. Open the output XML file and notice that the value of the **Status** field is set to **Approved**.  
  
7. Repeat steps 3 and 4 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**XYZ**).  
  
## Comments  
  
-   It is **very important** to remember that when you remove a policy from an application, you do not just remove the association between the application and the policy; you also delete the policy and its associated vocabulary from the rule engine database.  
  
-   When you start an application, by default, it deploys the policies automatically. Similarly, when you stop an application and select **Full Stop - Terminate Instances**, the associated policies are undeployed automatically. When you select **Partial Stop - Suspend running instances**, the associated policies are not undeployed automatically.  
  
-   You should refresh the views in Business Rule Composer and BizTalk Server Administration console to make sure you are looking at the latest information before performing any operation.  
  
-   If you create a new version of the policy whose earlier version is associated with a BizTalk application, you should manually add the new version of the policy to the application. You should not remove the old version of the policy unless you really want to delete it from the rule engine database.  
  
-   You can merge two or more BRL (Business Rule Language XML file) files into a single BRL file before importing. The following code shows three BRL files. The first BRL file contains the **POVocabulary** vocabulary. The second BRL file contains the **ProcessPurchaseOrder** policy. The third BRL file contains both the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy. The third BRE file is created by performing the following steps:  
  
    1.  Create a new file using any file editor and save it as an XML file (for example: POPolicyVocabulary.xml).  
  
    2.  Copy the entire XML content from the first BRL file containing the vocabulary.  
  
    3.  Copy the ruleset block (starts with the \<ruleset\> tag and ends with the \</ruleset\> tag) from the second BRL file.  
  
    4.  Save the new file. You can import this single XML file to create the **POVocabulary** vocabulary and the **ProcessPurchaseOrder** policy.  
  
    > [!NOTE]
    >  It does not matter in which order the vocabulary and ruleset nodes are listed in the merged BRL file. You can have the ruleset node ahead of the vocabulary node.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
    </brl>  
  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
    ```