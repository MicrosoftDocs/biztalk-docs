---
title: "Error Handling (BizTalk Server Samples Folder) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, errors"
  - "errors, examples"
  - "examples, messages"
  - "messages, examples"
  - "messages, errors"
ms.assetid: b39791ed-277b-4625-b9a9-72480a1b6ff6
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error Handling (BizTalk Server Samples Folder)
The purpose of this sample is to build an error-handling functionality for the content-based routing (CBR) application.  

## Prerequisites  
 To run the sample, it is recommended that you have Microsoft Office InfoPath 2010 or later installed. You can run the sample without using InfoPath, but in that case you cannot see the expense reports and the submission of expense reports through the HTTP adapter.  

## What This Sample Does  
 The sample implements part of an expense report processing system. Specifically, this sample does the following:  

1. Defines an expense report schema containing information about an expense report and the individual submitter including department name.  

2. Provides for the submission of the expense report through a directory or through a Web service using InfoPath.  

3. Promotes the **Department** and **correlationID** properties in the message document so that it can be used in a port filter to control routing.  

4. Routes expense reports belonging to the Marketing department to a file in a directory, simulating delivery to the department's back-end system.  

5. Generates a failed message for expense reports belonging to departments other than Marketing. The failed message includes information about the error including error code and error description.  

6. Routes failed messages to a human recipient (a business user or application operator) for correction and resubmission.  

7. Routes resubmitted expense reports based on department as described above.  

   Much of this work is done through a BizTalk orchestration schedule.  

## How This Sample is Designed and Why  
 The design relies on the default send and receive XML pipelines, property promotion, subscription filters, and orchestration schedules within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to route messages. Design elements and their justification are listed in the following table.  


|         Design element         |                                                                                                                                                                 Reason(s) selected                                                                                                                                                                 |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Default XML receive pipeline  |                                                        -   The XMLReceive pipeline supports property promotion; the PassThruReceive pipeline does not.<br />-   The inbound message is already in XML format and does not require processing beyond basic disassembly and party resolution.                                                        |
|  Routing for failed messages   | -   Receive ports suspend failed messages and generate a negative acknowledgment by default. When routing is enabled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attempts to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule). |
|       Property promotion       |                                                                                                   -   BizTalk Server depends upon property fields to do routing. Distinguished fields are used by orchestrations and cannot be used for routing.                                                                                                   |
|      Subscription filter       |                                                                                                          -   The subscription filter performs the routing by capturing messages that meet one or more criteria based on property fields.                                                                                                           |
| BizTalk orchestration schedule |                                                                  -   Provides the opportunity to add information to failed messages.<br />-   Enables routing of failed messages to a dedicated location for human intervention.<br />-   Processes resubmitted expense reports.                                                                   |
|          XMLTransmit           |                                                                                                                -   Performs basic assembly of outgoing XML messages. The PassThruTransmit pipeline provides no additional support.                                                                                                                 |

## Where to Find This Sample  
 This sample is located at <`Samples Path>`\Messaging\ErrorHandling\\.  

 The following table contains a list of files for this sample.  

|File|Description|  
|----------|-----------------|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache.<br /><br /> Removes send and receive ports.<br /><br /> Removes Internet Information Services (IIS) virtual directories as needed.|  
|ErrorHandling.sln|Visual Studio solution file for the sample.|  
|ErrorHandlingBinding.xml|Binding file for the sample.|  
|Setup.bat|Used to build and initialize this sample.|  
|Expense Report – John Doe.xml|Example expense report InfoPath document.|  
|Invalid Expense Report – John Doe.xml|Example expense report InfoPath document with invalid data in it.|  
|In ErrorHandler folder:<br /><br /> ErrorHandler.btproj|BizTalk project for orchestration.|  
|In ErrorHandler folder:<br /><br /> ResubmitLogic.odx|Orchestration that subscribes to failed messages, sends them to the human recipient for correction, and then resubmits corrected messages back into the server for routing.|  
|In ErrorHandler folder:<br /><br /> SuspendMessage.odx|Orchestration used for suspending messages that cannot be processed within the error-handling orchestration.|  
|In InfoPathForms folder:<br /><br /> Expense Report.xsn<br /><br /> Expense Report - Resubmit.xsn|Expense report InfoPath form and form used for viewing and resubmitting failed messages.|  
|In PipelinesAndSchemas folder:<br /><br /> ExpenseReportSchema.xsd|XML schema for the expense report document.|  
|In PipelinesAndSchemas folder:<br /><br /> PipelinesAndSchemas.btproj|BizTalk project for the sample.|  
|In PipelinesAndSchemas folder:<br /><br /> PropertySchema.xsd|Property schema for the sample.|  

## How to Use This Sample  
 This sample provides a starting point for creating your own error handling procedure.  

## Building and Initializing This Sample  

#### To build and initialize the Compose sample  

1. In a command window, navigate to the following folder:  

    <`Samples Path`>**\Messaging\ErrorHandling**  

2. Run **Setup.bat**, which performs the following actions:  

   - Creates three folders: **ExpenseReportIn**, **ExpenseReportOut**, and **ResubmittedReportIn** under the following path:  

      <`Samples Path`>**\Messaging\ErrorHandling**  

   - Copies and publishes the InfoPath forms **Expense Report.xsn** and **Expense Report – Resubmit.xsn** into the folder **C:\Temp\InfoPathForms**.  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  

   - Creates a virtual directory called **ExpenseReports**.  

   - Creates a new BizTalk application called **Error Handling Sample** and deploys the sample assemblies into it.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations, and the send and receive ports.  

   - Enlists and starts orchestrations, enables the receive locations, and starts the send ports.  

      If you choose to open and build the projects in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the sample assemblies.  

3. Before attempting to run this sample, confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build or initialization process.  

   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

4. If you are using Internet Information Services (IIS) 7.0, you need to perform additional configuration steps to adjust the setting for the virtual directory that corresponds to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP receive location used by the sample. Configure IIS by doing the following:  

   1. Using IIS 7.0 Manager, create a new application pool for the BizTalk Isolated Host Users group.  

   2. Configure the application pool to run under the identity of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Isolated Host user. (You may skip this step if you already have an application pool configured for other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP receive locations.)  

   3. Configure the virtual directory **ExpenseReport** to use the HTTP receive application pool created in the previous step.  

      If you do not already have a Web server extension for the BTSHTTPReceive.dll ISAPI extension, create and enable it by setting its status to "Allowed". You can do this in IIS 7.0 by using the IIS Management console (either directly under **Administrative Tools** or through the Computer Management console) as follows:  

   4. Expand the **Internet Information Services Manager** tree.  

   5. Click the **Web Service Extensions** folder.  

   6. In the right pane of the management console, click **Add a new Web Service extension**.  

   7. In the **New Web Service Extension** dialog box, click **Add**.  

   8. In the **Add file** dialog box, click **Browse** to select the file <`BizTalkInstallPath>`**\HttpReceive\BTSHTTPReceive.dll**, and then click **OK**.  

   9. Configure the virtual directory **ExpenseReport** to use local path [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HTTPReceive  

      For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).  

## Running the Sample  
 Before running the sample with the correct expense report, use the following procedure to verify that the "no errors" case sample works correctly.  

#### To verify that the "no errors" case sample works correctly  

1. Open the InfoPath form **Expense Report - John Doe.xml**. Look at the **Department** field within the form. This field should be set to "Marketing".  

2. In the upper-left corner of the InfoPath window, click **Submit** or click **Resubmit Expense Report**. Wait for a confirmation window that says the expense report was successfully submitted.  

    -OR-  

    Copy and paste this file into the **ExpenseReportIn** folder.  

3. You should see a new file dropped into the **ExpenseReportOut** folder. This file is the same expense report form that was submitted during previous steps.  

   After you confirm the "no errors" case, use the following procedure to run the sample with an incorrect expense report to trigger error-handling functionality.  

#### To trigger error handling  

1. Open the InfoPath form **Invalid Expense Report - John Doe.xml**. Look at the **Department** field within the form. This field is set to some invalid value.  

2. In the upper-left corner of the InfoPath window, click **Submit**. Wait for a confirmation window that says the expense report was successfully submitted.  

    -OR-  

    Copy and paste this file into the **ExpenseReportIn** folder.  

3. You should see a new file called **ErrorReport_\<**<em>date</em>_<em>time</em>**\>.xml** dropped into the **ExpenseReportOut** folder.  

    Open this file and observe that this is the expense report submitted in the previous step but with the error information added at the beginning.  

4. Replace the erroneous department value with "Marketing", and then click **Submit** in the upper-left corner of the InfoPath window.  

    -OR-  

    Copy and paste this file into the **ResubmittedReportIn** folder.  

5. You should see a new file created in the **ExpenseReportOut** folder. This file is the corrected expense report that was resubmitted into the server.  

## See Also  
 [Using Failed Message Routing](../core/using-failed-message-routing.md)   
 [Messaging (BizTalk Server Samples Folder)](../core/messaging-biztalk-server-samples-folder.md)