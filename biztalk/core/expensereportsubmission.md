---
title: "ExpenseReportSubmission | Microsoft Docs"
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
ms.assetid: d0bacab3-7092-44b8-a1c6-6f574a2db8bd
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExpenseReportSubmission
The ExpenseReportSubmission sample demonstrates how to submit a document to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration from a rich client such as Microsoft Excel.  

 Rich clients enable you to perform a number of actions, such as data validation and preliminary calculations, on the client. This helps to minimize interactions with the back-end server, which can be useful when only low bandwidth connections are available.  

## Prerequisites  
 You must ensure that your development environment is configured and enabled to work with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services. For more information, see [Enabling Web Services](../core/enabling-web-services.md).  

## What This Sample Does  
 This sample shows how you can submit an expense report to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directly from Excel, using the following sequence of steps:  

1. The user performs the manual sample steps provided in the Excel spreadsheet.  

2. Macro code in the spreadsheet converts the spreadsheet data to Extensible Markup Language (XML) format, and submits the XML message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using an HTTP connection.  

3. The computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retrieves the XML expense report message, validates its format using the provided schema, and then drops it into a different folder.  

4. In practice, beyond the scope of this sample, another application such as an Enterprise Resource Planning (ERP) system would then retrieve the spreadsheet file for further processing.  

## Where to Find This Sample  
 \<*Samples Path*\>\AdaptersUsage\ExpenseReportSubmission\  

 The following table shows the files in this sample and describes their purpose.  


|                                                            File(s)                                                            |                                                                                           Description                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                          Cleanup.bat                                                          | Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed. |
|                                                    ExpenseReport.15.3.xls                                                     |                                              Excel spreadsheet with the expense report layout, associated macros, and buttons to invoke the macros.                                              |
|                                                      MessageExample.xml                                                       |                                                                            Example of the XML expense report format.                                                                             |
|                                                           Setup.bat                                                           |                                                                               Builds and initializes this sample.                                                                                |
| In the \BTSExpenseDemo folder:<br /><br /> AssemblyInfo.cs,<br /><br /> BTSExpenseDemo.btproj,<br /><br /> BTSExpenseDemo.sln |                                                                  Provides project, solution, and related files for this sample.                                                                  |
|                             In the \BTSExpenseDemo folder:<br /><br /> BTSExpenseDemoBinding.xml                              |                                                                         Used for automated setup, such as port binding.                                                                          |
|                            In the \BTSExpenseDemo folder:<br /><br /> BTSExpenseOrchestration.odx                             |                                   Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for this sample.                                   |
|                              In the \BTSExpenseDemo folder:<br /><br /> SchemaExpenseReport.xsd                               |                                                                       Provides a schema for the XML expense report format.                                                                       |

### To build and initialize this sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\AdaptersUsage\ExpenseReportSubmission  

2. Run the file Setup.bat, which performs the following actions:  

   - Compiles the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample, and deploys the resulting assembly.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warnings when creating and binding the ports:  
     >   
     >  `Warning: Receive handler not specified for receive location "BTSExpenseReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`.  
     >   
     >  You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

   - Configures IIS.  

   - Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.  

   - Sets the HTTP address to the location expected by the Excel spreadsheet.  

   > [!NOTE]
   >  For more information about the BizTalk ISAPI filter, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  
   > 
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
   > 
   > [!NOTE]
   >  If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assembly.  
   > 
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

3. The setup.bat file configures the virtual directory for this sample to run in the IIS application pool associated with the default web site.  To configure the virtual directory for this sample to run under the context of a user in the **BizTalk Isolated Host Users** and **IIS_WPG** user groups, you should configure the virtual directory to run in a new IIS application pool.  Configure the virtual directory to run in a new IIS application pool by completing the following steps:  

   > [!NOTE]
   >  If you have already created a new application pool for another SDK sample then you can proceed to the last bullet item below.  

   1.  Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  

   2.  In the **Internet Information Services (IIS) Manager**, navigate to the **Application Pools** folder.  

   3.  Right-click the **Application Pools** folder and click **New**, **Application Pool...**  

   4.  Enter a name for the **Application Pool ID:** such as BizTalkSDKSamples, verify that the **Use default settings for new application pool** option is selected and click **OK** to create the new application pool.  

   5.  Right-click the new application pool and then click **Properties**.  

   6.  Click the **Identity** tab of the properties dialog box and change the identity under which this application pool runs to a user that is a member of the **BizTalk Isolated Host Users** user group.  This user should also be a member of the local **IIS_WPG** user group.  

   7.  Configure the virtual directory for this SDK sample to run under the new application pool. The **Application pool:** setting is available on the **Virtual Directory** tab of the Virtual Directory properties dialog box. The virtual directory created for this sample is **ExpenseReportSubmission**.  

4. Add a web service extension to IIS for HTTPReceive.dll  

   1.  In the **Internet Information Services (IIS) Manager**, navigate to the **Web Service Extensions** folder.  

   2.  Right-click the **Web Service Extensions** folder and select **Add a new Web service extension** to display the **New Web Service Extension** dialog box.  

   3.  Enter **ExpenseReportSubmission** for **Extension name:**  

   4.  Click **Add** to display the **Add file** dialog box.  

   5.  Click **Browse** to display the **Open** dialog box and navigate to *\<BizTalk Server Installation folder\>*\HttpReceive\BTSHTTPReceive.dll and click **Open**, then click **OK**.  

   6.  Enable the option to **Set extension status to Allowed** and click **OK**.  

## Running This Sample  
 Use the following procedure to run the ExpenseReportSubmission sample.  

> [!NOTE]
>  If you are using the enhanced security features of Microsoft Excel, the macros in the spreadsheet may be disabled. Follow the instructions provided by Excel about how to run unsigned macros from a trusted source.  

#### To run this sample  

1.  Open the Excel file ExpenseReport.15.3.xls included with this sample.  

2.  Optionally, change the sample data in the spreadsheet without changing its format.  

3.  In the spreadsheet, click **Start** to perform local calculations.  

     The text of the button changes from **Start** to **Submit**.  

4.  In the spreadsheet, click **Submit**.  

5.  Observe the text of the submitted message, the result above the table with yellow background (cell C7), and the actual return code and text description below and to the right (cell G23).  

     If submission fails, try again. Also, refer to the troubleshooting table in the Comments section.  

## Comments  
 Scenarios such as this can occur when, for example, a field sales force is equipped with older versions of Microsoft Windows that do not support the .NET Framework, and for which the requirement to upgrade to a more current version of Windows is not a viable option.  

 Essential features demonstrated in this sample are:  

- Submission from a rich client (not .NET-based)  

- Microsoft Office integration  

- HTTP receive connections  

- Simple orchestration  

- File adapter  

  The following table shows some possible submission errors and their solutions.  

|HTTP error code|Possible action|  
|---------------------|---------------------|  
|401 Unauthorized|Enable anonymous access on the virtual directory.|  
|503 Service Unavailable, and most other HTTP codes in the 400 and 500 ranges|Ensure that the host runs and that the service is deployed, bound to the correct port, and started.|  

## See Also  
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)