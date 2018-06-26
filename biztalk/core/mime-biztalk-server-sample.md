---
title: "MIME (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send pipelines, MIME/SMIME Encoder [pipeline component]"
  - "examples, send pipelines"
  - "MIME/SMIME Encoder [pipeline component], send pipelines"
  - "MIME/SMIME Encoder [pipeline component], examples"
  - "examples, MIME/SMIME Encoder [pipeline component]"
ms.assetid: f76c720d-3798-4f15-a5f9-885ddf421d57
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME (BizTalk Server Sample)
The MIME sample demonstrates how to perform MIME encoding within a send pipeline.  

## What This Sample Does  
 This sample configures the folder MIMEIn as a receive location. When you place a file, such as the sample file ImageInput.gif, in this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following steps:  

1.  Retrieve the message file from the receive location folder MIMEIn.  

2.  In the receive pipeline, pass the message through unchanged.  

3.  In the MessageBox database, route the message to the send pipeline.  

4.  In the send pipeline, perform MIME encoding and place the file into the send adapter folder MIMEOut.  

## Where to Find This Sample  
 \<*Samples Path*\>\Pipelines\MIME\  

 The following table shows the files in this sample and describes their purpose.  


|                           File(s)                            |                                                                                              Description                                                                                               |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         Cleanup.bat                          | Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed. |
|                        ImageInput.GIF                        |                                                                                           Sample input file.                                                                                           |
| SampleMimeEncoding.btproj<br /><br /> SampleMimeEncoding.sln |                                                                              Project and solution files for this sample.                                                                               |
|                SampleMimeEncodingBinding.xml                 |                                                                             Used for automated setup such as port binding.                                                                             |
|                     SendMimePipeline.btp                     |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send pipeline file with the MIME Encoder component.                                 |
|                          Setup.bat                           |                                                                               Used to build and initialize this sample.                                                                                |

## Building and Initializing This Sample  
 Use the following procedure to build and initialize the MIME sample.  

#### To build and initialize this sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\Pipelines\MIME  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (MIMEIn) and output (MIMEOut) folders for this sample in the folder:  

      \<*Samples Path*\>\Pipelines\MIME  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warning when creating and binding the ports:  

     > [!NOTE]
     >  `Warning: Receive handler not specified for receive location "MIMEReceiveLocation"; updating with first receive handler with matching transport type.`  

     > [!NOTE]
     >  You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

> [!NOTE]
>  If you run this sample from a location other than where it is installed, you must first add a reference to the **Microsoft.BizTalk.Pipeline.Components** assembly.  
> 
> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
> 
> [!NOTE]
>  If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assembly. To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running This Sample  
 Use the following procedure to run the MIME sample.  

#### To run this sample  

1.  Put a copy of the file ImageInput.gif into the folder MIMEIn.  

2.  Observe the text file created in the folder MIMEOut. The name of this text file is based on the message ID GUID. This file contains MIME-encoded content of the input file ImageInput.gif.  

## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)