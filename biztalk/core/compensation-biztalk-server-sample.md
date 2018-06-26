---
title: "Compensation (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "examples, orchestrations"
  - "compensations, examples"
  - "examples, compensations"
  - "compensations, orchestrations"
ms.assetid: 9d10c7be-6a4c-44cc-bf29-78ecdf147bd1
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Compensation (BizTalk Server Sample)
The Compensation sample demonstrates how to use the **Compensate** shape in an orchestration.  
  
## What This Sample Does  
 This sample demonstrates how to compensate the transaction that has already been committed in the orchestration using the following sequence of steps:  
  
1.  Enter the customer data in the InfoPath form and submit the data to an orchestration that has been exposed as a Web service.  
  
2.  The orchestration has two parallel actions. One returns an acknowledgment to the InfoPath form and the other updates the Northwind and BTSCompensationSampleMailingList databases.  
  
3.  In the second action, the orchestration maps the incoming message to a customer relationship management (CRM) application message format and then updates the **Customers** table in the Northwind database. After this, the Mailing List table in the BTSCompensationSampleMailingList database is updated.  
  
4.  If either update fails, the changes made to the Northwind database are compensated by calling an external assembly to write the original customer data back to the database.  
  
## How This Sample is Designed and Why  
 A **Scope** shape is primarily used for transactional execution and exception handling, including compensation. A scope consists of two blocks. The first block is the context block and the second block can be one or more exception-handling or compensation blocks. This is similar to the try-catch statement in the .NET programming language. In the UpdateContact.odx orchestration, there are two parallel actions. At the right-side branch, the try block is the **Scope** shape named Updated Backend Systems, which has a Long-Running transaction type and an Upd_Backend transaction identifier. Further down in the flow, there is a catch block that catches the general exception and initiates the compensation.  
  
 For more information about the **Scope** shape, see [Scopes](../core/scopes.md). Also see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).  
  
> [!NOTE]
>  The orchestration must itself be a long-running transaction for you to set the transaction type to Atomic or Long-Running.  
  
 In the try block, there are two scopes named **Update CRM** and **Update Mailing**. Both of these scopes are atomic transactions. In the Update CRM scope, there is a try block and a compensation block. The try block updates the Northwind database through a method call to an external assembly. The compensation block is where the compensation action takes place. When an exception happens in the Update Backend Systems scope, the code in Undo CRM Expression Shape updates the record back to its original state. This is triggered by the **Compensate** shape in the Catch Exception block.  
  
> [!NOTE]
>  Atomic transactions guarantee that any partial updates are rolled back automatically in the event of a failure during the transactional update, and that the effects of the transaction are erased (except for the effects of any .NET calls that are made in the transaction).  
  
> [!NOTE]
>  A long-running transaction is considered committed when the last statement in it has completed. There is no automatic rollback of state in case of a transaction abort. You can achieve this programmatically through the exception and compensation handlers demonstrated in this sample.  
  
 In the catch block, there is one **Delay** shape set for ten seconds. This delays the compensation action. There is also a **Compensate** shape that initiates the compensation action in the Upd_Backend transaction.  
  
 The following happens after the orchestration receives the input message:  
  
1.  The UpdateCrm assembly updates a row in the Northwind database.  
  
2.  The UpdateMailingList assembly updates a matching record in the BTSCompensationSampleMailingList database.  
  
3.  In the event of a failure while updating the Northwind database, an exception is raised and the orchestration exits the process.  
  
4.  In the event of a failure while updating the BTSCompensationSampleMailingList database, an exception is raised and a ten-second delay takes place before rewriting the original customer data back to the Northwind database.  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Orchestrations\Compensation\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Batch file used to uninstall the sample.|  
|CompensationOrchestration.btproj|Orchestration project.|  
|CompensationSample.sln|Sample solution.|  
|CompensationSampleBinding.xml|Binding data for the orchestration (used during installation).|  
|ContactInfo.xsd|Contact information message schema.|  
|ContactInfo.xsx|Orchestration Designer layout file.|  
|CreateSQLDataStore.sql|SQL script to create and populate the sample database.|  
|CrmSchema.xsd|CRM update message schema.|  
|MailingListSchema.xsd|Mailing list message update schema.|  
|RemoveVirDir.vbs|Microsoft Visual Basic Scripting Edition (VBScript) script to remove Web service virtual and physical directories (used during uninstallation).|  
|Request2Crm.btm|Message map to translate from request (contact info) to CRM update message.|  
|Request2MailingList.btm|Message map to translate from request (contact info) to mailing list message.|  
|Setup.bat|Batch file to install this sample.|  
|UpdateContact.odx|Orchestration file.|  
|UpdateRequest2UpdateResponse.btm|Message map to translate from request (contact info) to a response message.|  
|UpdateResponse.xsd|Response message schema.|  
|InfoPath\Contact Info Update.xsn|Microsoft InfoPath file used to submit forms to the orchestration Web service.|  
|UpdateCrm\AssemblyInfo.cs|Assembly information source file for the UpdateCrm assembly. (The UpdateCrm assembly updates the Northwind database.)|  
|UpdateCrm\UpdateCrm.cs|Main source code for the UpdateCrm assembly.|  
|UpdateCrm\UpdateCRM.csproj|UpdateCrm project file.|  
|UpdateMailingList\AssemblyInfo.cs|Assembly information source file for the UpdateMailingList assembly. (The UpdateMailingList assembly updates the sample database.)|  
|UpdateMailingList\UpdateMailingList.cs|Main source code for the UpdateMailingList assembly.|  
|UpdateMailingList\UpdateMailingList.csproj|UpdateMailingList project file.|  
  
## Building and Initializing This Sample  
  
#### To build and initialize the Compensation sample  
  
1. In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Orchestrations\Compensation\  
  
2. Run Setup.bat, which performs the following actions:  
  
   -   Build and deploy the sample assembly.  
  
   -   When the BizTalk Web Services Publishing Wizard launches, do the following manually:  
  
   1.  On the **Welcome to the BizTalk Web Services Publishing Wizard** page, click **Next**.  
  
   2.  On the **Create Web Service** page, select **Publish BizTalk orchestration as web services**, and then click **Next**.  
  
   3.  On the **BizTalk Assembly** page, browse and select \<*Samples Path*\>\Orchestrations\Compensation\bin\Release\CompensationOrchestration.dll, and then click **Next**.  
  
   4.  On the **Orchestrations and Ports** page, click **Next**.  
  
   5.  On the **Web Service Properties** page, in **Target namespace of web service**, type **http://Microsoft.BizTalk.Samples.Compensation/**, and then click **Next**.  
  
   6.  On the **Web Service Project** page, in **Location**, type **http://localhost/CompensationOrchestrationWebServiceProxy**.  
  
   7.  Select the **Allow anonymous access to web service** check box.  
  
   8.  Select the **Create BizTalk receive location in the following application** check box.  
  
   9. In the **Create BizTalk receive location in the following application** drop-down menu, select **BizTalk Application 1** from the drop-down list, and then click **Next**.  
  
   10. On the **Web Service Project Summary** page, click **Create**.  
  
   11. On the **Completing the BizTalk Web Services Publishing Wizard** page, click **Finish**.  
  
3. Setup creates and binds ports, creates the back-end database for the sample, and adds C# assemblies to the global assembly cache.  
  
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
  
## Running This Sample  
 After you build and initialize this sample, consider the following before you run it:  
  
- If you are running this sample on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], you must create an IIS application pool and set its identity to an account that is a member of the BizTalk Application Users Windows group. You also need to update the orchestration Web service virtual directory to run within this application pool.  
  
- Add the ASPNET account to the BizTalk Isolated Host Users group.  
  
- Give the BizTalk Application Users group db_owner permission to the **BTSCompensationSampleMailingList** and **Northwind** databases.  
  
- If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not installed in the default location (drive:\Program Files\Microsoft BizTalk Server \<version\>\\), you must publish the Contact Info Update.xsn form before using it. To do so, do the following.  
  
  #### To publish the InfoPath form  
  
  1.  In Internet Explorer, on the **Tools** menu, click **Internet Options**.  
  
  2.  On the **Security** tab, click **Internet**, and then click **Custom Level**.  
  
  3.  In the **Miscellaneous** section, ensure that the **Access data sources across domains** setting is enabled, and then click **OK**. This setting is required for the InfoPath user interface solution scripting code to run.  
  
  4.  In Windows Explorer, navigate to \<*Samples Path*\>\Orchestrations\Compensation\InfoPath, right-click **Contact Info Update.xsn** and then click **Design**.  
  
  5.  The InfoPath Contact Info Update solution opens in design mode.  
  
  6.  In the InfoPath Contact Info Update application, on the **File** menu, click **Publish**.  
  
  7.  The Publish Wizard appears.  
  
  8.  Select **To a shared folder on this computer or on a network** and publish the solution to the path \<*Samples Path*\>\Orchestrations\Compensation\InfoPath\Contact Info Update.xsn.  
  
  9. Close the design mode InfoPath.  
  
- You are ready to run this sample.  
  
  #### To run the Compensation sample  
  
  1.  Double-click **Contact Info Update.xsn** to open it in InfoPath.  
  
  2.  Fill out the form for an account that exists in both databases. For example, use an existing account ID "ALFKI" from the Northwind Customers table.  
  
  3.  On the **File** menu, select **Submit**, and click **Submit**.  
  
  4.  The response document should appear in the \<*Samples Path*\>\Orchestrations\Compensation\Out folder, and both the Northwind and the BTSCompensationSampleMailingList databases should be updated with the new data from the InfoPath form.  
  
      > [!NOTE]
      >  You can detach the BTSCompensationSampleMailingList database or take it offline to test the compensation action that the orchestration performs. Observe that the record is updated in the Northwind database first. Then, when the orchestration tries to update the BTSCompensationSampleMailingList database, because that database is detached, the update fails. Therefore, an exception is raised and there is a ten-second delay before the compensation action takes place to write the original customer data back to the Northwind database.  
  
      > [!NOTE]
      >  You may get a "Login failed for user 'IIS APPPOOL\DefaultAppPool' error. It might be because of the token-based server access validation failure. To resolve this error, create a new application pool and use the administrator account in it.  
  
## Uninstalling This Sample  
  
#### To uninstall the Compensation sample  
  
1. In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Orchestrations\Compensation\  
  
2. Run Cleanup.bat.  
  
## See Also  
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)