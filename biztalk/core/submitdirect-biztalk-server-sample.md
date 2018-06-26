---
title: "SubmitDirect (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, receive adapters"
  - "receive adapters, examples"
  - "examples, receive adapters"
ms.assetid: 3540368b-cf46-4c83-a87b-94aec9cd1b36
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SubmitDirect (BizTalk Server Sample)
The SubmitDirect sample demonstrates how to programmatically submit one-way and request/response messages to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from .NET-based applications. The sample demonstrates the use of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] APIs for adapters. It also provides a receive adapter, named Submit, that can be used to submit messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## Prerequisites  
 Before running this sample, ensure you are logged on as a user who belongs to BizTalk Isolated Host Users group.  

## What This Sample Does  
 This sample shows how to perform various tasks related to BizTalk adapters. Specifically, it shows how to:  

- Work with isolated adapters that run outside of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process. The Submit adapter is an isolated adapter because it is created by a process external to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process (you start it as a .NET application).  

- Submit batches of messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The Submit adapter uses batch message submittal functionality to submit several messages at once.  

- Submit messages synchronously using a request/response paradigm, as well as asynchronously using a one-way paradigm.  

- Register an adapter with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This sample shows how to register an adapter and provides a registration executable that automates the registration of an adapter.  

  This sample is actually two samples in one, as follows:  

- **Submission of a batch of one-way messages.** The console application SubmitMessages.exe takes the strings from its command line and submits each one as a separate message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Each of these submitted messages is picked up at the receive location by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], sent through pass-through receive and send pipelines, and then written to a text file.  

- **Submission of request/response message.** The console application SubmitRequest.exe takes the .xml file specified on its command line and submits it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The schema of this .xml file defines elements that contain two integer fields. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] picks up the .xml file and processes it with an orchestration (with one request/response port). It uses a map to produce an XML response message that returns an integer that is the product of the two integers in the request. When the console application receives the response, it displays the result.  

## Where to Find This Sample  
 \<*Samples Path*\>\AdaptersDevelopment\SubmitDirect\  

 The following table lists the files in this sample and describes their purpose.  


|                                                                                                                     File(s)                                                                                                                      |                                                                                              Description                                                                                               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                   Cleanup.bat                                                                                                                    |    Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.    |
|                                                                                                                    Setup.bat                                                                                                                     |                                                                                  Builds and initializes this sample.                                                                                   |
|                                                                                                                 SubmitDirect.sln                                                                                                                 |                                Solution file that includes the BizTalk project in the ProcessRequest folder and the Microsoft Visual C# projects in the other folders.                                 |
|                                                                                               SubmitMessagesBinding.xml, SubmitRequestBinding.xml                                                                                                |                                                                             Used for automated setup such as port binding.                                                                             |
|                                                              In the \ProcessRequest folder:<br /><br /> DocIn.xsd, DocOut.xsd, Multiplier.odx, Multiply.btm, ProcessRequest.btproj                                                               |                                               Provides a BizTalk project that performs the multiplication of integers in the request/response scenario.                                                |
|                                                                       In the \SubmitMessages folder:<br /><br /> AssemblyInfo.cs, SubmitMessages.cs, SubmitMessages.csproj                                                                       |                                Provides a Visual C# project for the console application that passes its command line string parameters as a batch of separate messages.                                |
|                                                                In the \SubmitRequest folder:<br /><br /> AssemblyInfo.cs, DocInstance.xml, SubmitRequest.cs, SubmitRequest.csproj                                                                |                                 Provides a C# project for the console application that passes an .xml file (DocInstance.xml) containing two integers to be multiplied.                                 |
| In the \TransportProxyUtils folder:<br /><br /> AssemblyInfo.cs, MessageHelper.cs, MessagingAPIInterface.cs, MessagingAPIs.cs, ResponseCallBack.cs, TpBatchAsyncCallback.cs, TpBatchAsyncResult.cs, TpBatchStatus.cs, TransportProxyUtils.csproj | Provides a C# project for the run-time portion of the Submit adapter that implements methods for synchronous and asynchronous message submission, and for batch and single request message submission. |
|                                                              In the \TransportProxyUtilsReg folder:<br /><br /> AssemblyInfo.cs, RegisterAdapter.cs, TransportProxyUtilsReg.csproj                                                               |           Provides a Visual C# project that demonstrates code that you can use to register adapters with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].           |
|                                                           In the \TransportProxyUtilsUI folder:<br /><br /> AssemblyInfo.cs, TransportProxyUtilsMgmt.cs, TransportProxyUtilsUI.csproj                                                            |                                                           Provides a Visual C# project for the user interface portion of the Submit adapter.                                                           |

## Building and Initializing the Sample  

#### To build and initialize the SubmitDirect sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\AdaptersDevelopment\SubmitDirect  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the following output folder for the batch submission portion of this sample.  

      \<*Samples Path*\>\AdaptersDevelopment\SubmitDirect\Out  

   - Compiles the various [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  

   - Registers the Submit adapter with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations, and the send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warnings when creating and binding the ports:  
     >   
     >  `Warning: Receive handler not specified for receive location "SubmitDirectRL"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.ProcessRequest.Multiplier"; updating with first available host.`  
     >   
     >  You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive locations, and starts the send ports and orchestration.  

     > [!NOTE]
     >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
     > 
     > [!NOTE]
     >  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assemblies.  
     > 
     > [!NOTE]
     >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running the Sample  
 Because this sample uses File adapter, the BizTalk host (BizTalkServerApplication) must be running. Use the following procedures to run the SubmitDirect sample.  

#### To run the batch submission portion of the SubmitDirect sample  

1.  In a command window, navigate to the following folder:  

     \<*Samples Path*\>\AdaptersDevelopment\SubmitDirect\SubmitMessages\bin\Debug  

2.  Run the file SubmitMessages.exe, passing multiple strings on the command line.  

     Example: SubmitMessages msg1 msg2 msg3  

3.  Observe the multiple text files created in the output folder Out. These files contain the strings passed on the command line, one per file.  

#### To run the request/response portion of the SubmitDirect sample  

1.  In a command window, navigate to the following folder:  

     \<*Samples Path*\>\AdaptersDevelopment\SubmitDirect\SubmitRequest\bin\Debug  

2.  Run the file SubmitRequest.exe, passing an appropriate .xml file name on the command line.  

     Example: SubmitRequest ..\\..\DocInstance.xml  

3.  Observe the response XML message, containing the result of the multiplication operation, displayed to the console.  

## Comments  
 You can use the Submit adapter in other applications. You can use it from any .NET-based code to submit messages to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] programmatically. To use this adapter with your code, use the following procedure.  

#### To use the sample adapter with your code  

1. Register the Submit adapter with your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. If you have run the file Setup.bat provided with this sample, the adapter should be registered and ready to use. Otherwise, you can register it by building the projects TransportProxyUtils.csproj, TransportProxyUtilsUI.csproj, and TransportProxyUtilsReg.csproj, and then running the executable produced by the latter project, RegisterAdapter.exe.  

   > [!IMPORTANT]
   >  If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **RegisterAdapter.cs** file.  

2. Create a receive port with a receive location that uses the Submit adapter. Specify the address of the receive location. The address can be any string that is unique within the receive locations that use this adapter.  

3. Reference the assembly Microsoft.BizTalk.SDKSamples.AdaptersDevelopment.TransportProxyUtils.dll in your [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project.  

4. Submit messages to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using one or more of the following methods provided by this assembly.  


   |                                                Method(s)                                                |                                                                                                                                                                                       Description                                                                                                                                                                                       |
   |---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **SubmitMessage()**<br /><br /> **BeginSubmitMessage()**<br /><br /> **EndSubmitMessage()**       |              Synchronous and asynchronous methods to submit a one-way message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The address of the receive location where the message is submitted must be set on the message context.<br /><br /> A Boolean value indicating the status of submission (success/failure) is returned.              |
   |     **SubmitMessages()**<br /><br /> **BeginSubmitMessages()**<br /><br /> **EndSubmitMessages()**      | Synchronous and asynchronous methods to submit an array of one-way messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The addresses of the receive locations where the messages are submitted should be set on the context of the messages.<br /><br /> A Boolean value indicating the status of submission (success/failure) is returned. |
   | **SubmitSyncMessage()**<br /><br /> **BeginSubmitSyncMessage()**<br /><br /> **EndSubmitSyncMessage()** |                                     Synchronous and asynchronous methods to submit a request message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The address of the receive location where the message is submitted should be set on the message context.<br /><br /> The response message is returned.                                      |
   |                                      **CreateMessageFromString()**                                      |                                                                     Creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message object from a string and sets the receive location address property on the message context.<br /><br /> Returns a BizTalk message object.                                                                      |
   |                                      **CreateMessageFromStream()**                                      |                                Creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message object from a stream and sets the receive location address property on the message context.<br /><br /> Returns a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message object.                                |

    For details about the parameter and return types for these methods, see the file MessagingAPIInterface.cs in the TransportProxyUtils folder.  

## See Also  
 [Adapter Samples - Development](../core/adapter-samples-development.md)   
 [Registering an Adapter](../core/registering-an-adapter.md)