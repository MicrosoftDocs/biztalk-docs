---
title: "OperationsSamples (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c9e3f3e-a570-4edd-aa2e-3f8e2e37c8a0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# OperationsSamples (BizTalk Server Sample)
The OperationsSamples sample demonstrates how to perform operational activities using the Operations object model.  
  
## What This Sample Does  
 This sample demonstrates the following:  
  
- How to use a tracking profile to comment an orchestration with activities.  
  
- How to use the BAM tracking database to find an activity ID and then use the ID to find a related orchestration instance.  
  
- How to find and work with message flows by using the **MessageFlow** class and other Operations object model classes and APIs.  
  
- How to access ports, messages, and other instances by using classes derived from the **Instance** class.  
  
  The sample contains many useful helper classes and methods to support the operations above. These and other code highlights are discussed in the next section.  
  
## How This Sample Is Designed and Why  
 This sample is designed to demonstrate several of the key classes and methods in the Operations object model and to show how to query the publicly available BAM tracking database.  
  
 The Operations object model contains classes that provide the ability to manipulate messages and other instances within BizTalk Server.  
  
### Using a BAM Activity ID  
 This sample shows how to interact with BAM and how to use the publicly available views in the tracking database to locate a live message in the message box by using business data. The sample does this by retrieving an orchestration ID corresponding to a purchase order number. For this task to succeed, it must do the following:  
  
1. Use business data (a purchase order number) to find an activity ID. This step maps business data to an internal ID that can be used to find additional information.  
  
2. Retrieve the BAM references related to the activity ID.  
  
3. Find a reference that has a type of "BizTalkService" and refers to an orchestration. If one is found, return its instance ID.  
  
   This functionality is provided by the **BAMWebService.GetOrchestrationID** static method and associated helper methods including classes and methods in the BamManagementService.cs source file.  
  
### Suspending, Terminating, and Resuming an Instance  
 The sample program includes a **Samples.OperateOnInstance** method that takes an operation and instance ID and performs the specified operation on the instance. Valid operations are defined by the **InstanceOperation** enumeration and include Suspend, Terminate, and Resume. These operations map directly to methods of the BizTalkOperations class—**SuspendInstance**, **TerminateInstance**, and **ResumeInstance**.  
  
 Notice that the method handles both ArgumentException and SqlException exceptions. You must be careful to anticipate exceptions—including SqlException—when working with the classes and methods in the Operations object model.  
  
> [!NOTE]
>  Many of the Operations methods require access to the database. You should anticipate the exceptions thrown by these methods and handle them appropriately.  
  
### Retrieving All Live Messages  
 The Operations object model makes it straightforward to iterate over all of the available live messages, as shown in the following code fragment:  
  
```  
BizTalkOperations _operations = new BizTalkOperations()  
IEnumerable messages = _operations.GetMessages();  
foreach (BizTalkMessage msg in messages)  
…  
```  
  
 The OperationsSamples program takes this a step further by demonstrating how to access information about each message, including message ID and message type along with the number and types of message parts. You can modify this code and use it in scenarios where you have to iterate through many or all of the available live messages in BizTalk Server.  
  
> [!NOTE]
>  There may be hundreds or thousands of messages available. Scanning the entire list may adversely affect performance.  
  
## Where to Find This Sample  
 The sample is located in the following SDK location:  
  
 \<*Samples Path*\>\Admin\OperationsOM\OperationsSamples\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|BamManagementService.cs|Web proxy class for the BAM Web service.|  
|Cleanup.bat|Removes the sample orchestration and restores the HelloWorld sample to its original state.|  
|HelloOrchestration.btt|Tracking profile used to map BizTalk event sources to BAM target activities.|  
|HelloOrchestration.xls|BAM definition style sheet.|  
|OperationsSamples.cs|C# source file containing code that demonstrates various aspects of the Operations object model.|  
|OperationsSamples.csproj, OperationsSamples.sln, AssemblyInfo.cs|Project, solution, and assembly information files for this sample.|  
|Setup.bat|Used to build and initialize this sample by modifying the HelloWorld orchestration sample. It installs a sample orchestration, deploys a BAM Activity Definition and a Tracking Profile Editor file, configures ports, and drops a sample file into the receive location.|  
  
## How to Use This Sample  
 Use this sample to explore the functionality available in the Operations object model. Modify existing routines to find and work with messages differently or add new code that replicates portions of the Group Hub in the BizTalk Server Management console.  
  
 You may also consider some of the following tasks:  
  
-   Write an application that replicates the most-used subset of the Group Hub into a custom application.  
  
-   Write a custom provisioning application that creates ports and sends a test message through for new trading partners.  
  
-   Modify the sample program into a command-line utility that provides information about a single purchase order or a range of purchase orders to the screen, an XML file, or a text report.  
  
## Installing Sample Support Files  
 This section walks through the procedures required to install and run the sample.  
  
> [!NOTE]
>  Before installing and running this sample, you must verify that BAM has been installed and is functioning. If BAM has not been installed, this sample will not work.  
  
#### To compile and install the support files for this sample  
  
1.  In a command window, navigate to the following folder:  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
2.  Run Setup.bat, which performs the following actions:  
  
    -   Creates send and receive directories  
  
    -   Creates and starts send and receive ports  
  
    -   Compiles and deploys the HelloWorld orchestration in the `<Samples Path>`\Orchestrations\HelloWorld folder.  
  
    -   Modifies the public key token for the HelloWorld orchestration  
  
    -   Deploys the BAM Activity Definition and Tracking Profile Editor file  
  
    -   Renames the out directory  
  
    > [!NOTE]
    >  To abort the installation, press CTRL+C at the first "press any key to continue" prompt. This stops the script and leaves the HelloWorld sample in its original state. Pressing CTRL+C on the second and final prompt does not stop the installation. In this case, run Cleanup.bat to uninstall the OperationsOM sample and restore the HelloWorld sample.  
  
## Running This Sample  
 Use the following procedure to run the OperationsOM sample.  
  
#### To compile and run the sample  
  
1.  Click **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.  
  
3.  Right-click **BizTalkServerApplication**, and then click **Restart**.  
  
    > [!NOTE]
    >  Restarting the BizTalkServerApplication host instance may be necessary to set the correct working database for BAM if you have not restarted the host instance since configuring the product.  
  
4.  From Windows Explorer, navigate to the following folder:  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
5.  Double-click the **OperationsOM.sln** project file to load it into Visual Studio.  
  
6.  Press F5 to run the sample.  
  
     -- OR --  
  
     On the **Build** menu, click **Rebuild Solution**. When the build is complete, use Windows Explorer to navigate to `<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,` and then double-click **OperationsSamples.exe**.  
  
## Classes or Methods Used in This Sample  
 [Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124; [Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124; [Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124; [Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124; [Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124; [Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124; [Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)  
  
## See Also  
 [Admin-OperationsOM (BizTalk Server Samples Folder)](../core/admin-operationsom-biztalk-server-samples-folder.md)