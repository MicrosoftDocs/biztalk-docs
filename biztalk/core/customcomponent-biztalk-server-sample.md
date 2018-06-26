---
title: "CustomComponent (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], examples"
  - "examples, pipeline components [custom]"
  - "messages, streamed"
  - "pipeline components [custom], configuring"
ms.assetid: ed0da9f5-8cc7-4528-be8c-35b80744fd38
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CustomComponent (BizTalk Server Sample)
The CustomComponent sample demonstrates how to create and use a custom pipeline component that modifies a streamed message. This sample also demonstrates the configuration of a custom pipeline component in Pipeline Designer.  

## What This Sample Does  
 This sample implements a custom pipeline component that can prefix or append strings to the input message. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in streaming mode, meaning that the entire message is never loaded into memory. The custom pipeline component is demonstrated using the following sequence of steps:  

1. BizTalk retrieves a text message from a file in a specific folder.  

2. The text message is sent through a receive pipeline containing the FixMsg custom pipeline component. You configure this component to insert a string at the beginning of the message.  

3. You send the resulting text message through a send pipeline with the FixMsg custom pipeline component. You configure the component to append a string to the end of the message.  

4. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] writes the resulting text message to a file in a specific folder.  

## Where to Find This Sample  
 \<*Samples Path*\>\Pipelines\CustomComponent\  

 The following table shows the files in this sample and describes their purpose.  


|                                                     File(s)                                                     |                                                                                              Description                                                                                               |
|-----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                   Cleanup.bat                                                   | Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed. |
|                                                    Input.txt                                                    |                                                                                           Sample input file.                                                                                           |
|                                                    Setup.bat                                                    |                                                                               Used to build and initialize this sample.                                                                                |
|                  In the \FixMsg folder:<br /><br /> AssemblyInfo.cs, FixMsg.csproj, FixMsg.sln                  |                                              Project, solution, and assembly information files for the custom pipeline component portion of this sample.                                               |
|                                  In the \FixMsg folder:<br /><br /> FixMsg.cs                                   |                                                                             Implements the pipeline component interfaces.                                                                              |
|                               In the \FixMsg folder:<br /><br /> FixMsgStream.cs                                |                                                      Implements a wrapper for the **System.IO.Stream** class, enabling stream processing of data.                                                      |
|                             In the \FixMsg folder:<br /><br /> FixMsgDescription.cs                             |                                                       Provides methods for accessing and rendering component UI resources in Pipeline Designer.                                                        |
|                                 In the \FixMsg folder:<br /><br /> FixMsg.resx                                  |                                                                      Contains property descriptions, an icon, and error messages.                                                                      |
| In the \PipelineComponentSample folder:<br /><br /> PipelineComponentSample.btproj, PipelineComponentSample.sln |                                                               Project and solution files for the BizTalk project portion of this sample.                                                               |
|             In the \PipelineComponentSample folder:<br /><br /> PipelineComponentSampleBinding.xml              |                                                                             Used for automated setup such as port binding.                                                                             |
|      In the \PipelineComponentSample folder:<br /><br /> FixMsgReceivePipeline.btp, FixMsgSendPipeline.btp      |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines containing the FixMsg custom pipeline component, for the receive and the send pipelines, respectively.   |

## Building and Initializing This Sample  

#### To build and initialize the CustomComponent sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\Pipelines\CustomComponent  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (In) and output (Out) folders for this sample in the folder:  

      \<*Samples Path*\>\Pipelines\CustomComponent  

   - Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warnings when creating and binding the ports:  
     >   
     >  `Warning: Receive handler not specified for receive location "PCReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "CustomComponent"; updating with first available host.`  
     >   
     >  You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
> 
> [!NOTE]
>  If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair is used to sign the resulting assemblies.  
> 
> [!NOTE]
>  To undo changes made by Setup.bat, you must first stop and restart the host instance from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration MMC console. Next, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running This Sample  

#### To run the CustomComponent sample  

1.  Paste a copy of the text file Input.txt into the folder In.  

2.  Observe the text file created in the folder Out. This file contains the contents of the file Input.txt with additional text inserted at the beginning (by the receive pipeline) and at the end (by the send pipeline). The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.  

## Comments  
 You can view the preconfigured pipelines in Pipeline Designer by following these steps:  

1.  In Solution Explorer, double-click ReceivePipeline.btp to open the receive pipeline in Pipeline Designer. Observe that the FixMsg component is placed in the **Validate** stage of the receive pipeline.  

2.  Click the FixMsg component in the **Validate** stage on the design surface. In the Properties window, you can see the configuration properties of the pipeline component. Observe that the **PrependData** property is set to **Data to prepend in receive pipeline string**.  

3.  In Solution Explorer, double-click SendPipeline.btp to open the send pipeline in Pipeline Designer. Observe that the FixMsg component is placed in the **Pre-Assemble** stage of the send pipeline.  

4.  Click the FixMsg component in **Pre-Assemble** stage on the design surface. Note that the **AppendData** property is set to **Data to append in send pipeline string**.  

## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)