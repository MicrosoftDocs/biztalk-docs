---
title: "Enabling Validation of Bank Identifier Codes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bank Identifier Code (BIC), enabling"
ms.assetid: d268a892-f304-44cb-b590-28ef359c8d99
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enabling Validation of Bank Identifier Codes
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] schemas ensure that the Bank Identifier Codes (BICs) specified in the SWIFT interchange document conform to the SWIFT-defined BIC data format. A4SWIFT also supports validating the BICs against a customer-specified BIC list in a database.  

 You can perform this validation if you have enabled BRE validation and then enabled BIC validation.  

 By default, A4SWIFT Setup disables BRE validation. To enable it, you must set the BRE validation configuration parameter to true for a receive pipeline that uses the A4SWIFT disassembler. You must also run the BRE Deployment Utility to deploy the master policy and validation policy specific to the message to be validated (MT*xxx*_Master_policy.xml and MT*xxx*_Validation_Policy.xml). For more information, see [Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md) and [Deploying BRE Rules](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).  

 After you have enabled BRE validation, you must use publish and deploy both BIC validation policies (BIC_Master_Policy.xml and BIC_Validation_Policy.xml) using the Rules Engine Deployment Wizard. Before doing so, you must do the following:  

- Populate the database with BIC values from SWIFT. You can use the Bicplus table in the A4SWIFT database, which is installed by A4SWIFT Setup, or you can use your own custom database. For more information, see [Managing the Bicplus Table in the A4SWIFT Database](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md).  

- Set the BIC database and enable BIC validation by customizing the BIC Master Policy. See the procedure below.  

  For better performance, you should not deploy the BIC validation policies if BIC validation is not required.  

> [!NOTE]
>  You can publish and deploy the BIC validation policy only if you have published the A4SWIFT_Codelist and A4SWIFT_Functions vocabularies. Publish these vocabularies by running the BRE Deployment Utility on the SWIFTSchemas assembly. For more information, see [Lesson 1: Deploying the Related Business Rules](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md).  

### To customize the BIC Master Policy  

1. Open an XML editor (such as Notepad), and browse to **<*drive*Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies**.  

2. Open **BIC_Master_Policy.xml**. Replace the following existing strings with new values.  

   > [!NOTE]
   >  You must enter values for either the Bicplus table in the A4SWIFT database or your own custom database. The A4SWIFT database is not the default in BIC_Master_Policy.xml.  

   > [!NOTE]
   >  The following strings must not be contained within double quotes.  

   |            Existing string            |                                                              Replace with                                                              |
   |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
   |      **SPECIFY SQL SERVER NAME**      | The name of the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] containing the database holding the BIC. |
   |     **SPECIFY BIC DATABASE NAME**     |                                         The name of the database that contains the BIC table.                                          |
   | **SPECIFY INTEGRATED SECURITY VALUE** |                                                                **SSPI**                                                                |


3. Save the modified Master Policy.  

4. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.  

5. On the Welcome page, click **Next**.  

6. On the Deployment Task page, click **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.  

7. On the Policy Store page, in **SQL Server Name**, select the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that contains your BizTalk databases. In **Configuration Database on selected server**, select **BizTalkRuleEngineDb**, and then click **Next**.  

8. In the Import Rules Engine Policy/Vocabulary file page, browse to **<*drive*\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies**, click **BIC_Master_Policy.xml**, click **Open**, and then click **Next**.  

9. On the Ready page, verify the data, and then click **Next**.  

10. On the Importing Policy/Vocabulary page, verify that the command succeeded, and then click **Next**.  

11. On the Completing the Rules Engine Deployment Wizard page, click **Run this wizard again**, and then click **Finish**.  

12. On the Welcome page, click **Next**.  

13. On the Deployment Task page, click **Deploy Policy**, and then click **Next**.  

14. On the **Policy Store** page, in **SQL Server Name**, select the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that contains your BizTalk databases. In **Configuration Database on selected server**, select **BizTalkRuleEngineDb**, and then click **Next**.  

15. On the **Deploy Policy** page, select **BIC_Master_Policy.1.0**, and then click **Next**.  

16. On the **Ready** page, click **Next**.  

17. On the Deploying Policy page, if the deployment has succeeded, click **Next**. Click **Run this wizard again**, and then click **Finish**.  

18. Repeat steps 5 through 17 for **BIC_Validation_Policy.xml**, entering **BIC_Validation_Policy** instead of **BIC_Master_Policy**.  

19. Exit the Rules Engine Deployment Wizard.  

20. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**. Verify that the **Policies** list includes **BIC_Master_Policy** and **BIC_Validation_Policy** under **Policies**.  

21. Expand **Version 1.0 - Deployed** under **BIC_Master_Policy**, and then click **BIC_Master_Rule**.  

22. In the THEN pane, verify that the SQL Connection properties listed are correct.  

    > [!NOTE]
    >  A4SWIFT does not pick up changes made to the master BIC validation policy until you restart the BizTalk service that hosts the receive pipeline that is currently configured to use the SWIFT disassembler. A4SWIFT validates all documents that pass through this pipeline for the BIC values that are contained in the BIC column specified in the BIC master policy. The user account used to start this BizTalk service (BTSNTSvc.exe) must have access to the BIC database and table. For better security, it is recommended that you grant read-only access to the BIC database and table.  

    > [!NOTE]
    >  If you are using Message Repair and New Submission, the World Wide Web Publishing service must be restarted (by running iisreset.exe) for BIC validation to work from InfoPath.  

## See Also  
 [Working with BRE Policies](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)   
 [Managing the Bicplus Table in the A4SWIFT Database](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)