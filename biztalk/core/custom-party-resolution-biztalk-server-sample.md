---
title: "Custom Party Resolution (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, parties"
  - "pipeline components [custom], examples"
  - "pipeline components [custom], parties"
  - "examples, pipeline components [custom]"
  - "parties, pipeline components [custom]"
  - "parties, custom"
ms.assetid: 1f88450f-5fe9-486d-bfb8-fd11181c78b4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Party Resolution (BizTalk Server Sample)
The Custom Party Resolution sample demonstrates how to write a custom pipeline component to resolve a custom party.  
  
## What This Sample Does  
 The Custom Party Resolution sample accomplishes its task using the following sequence of steps:  
  
1.  An XML document is retrieved from a folder.  
  
2.  The pipeline resolves the party.  
  
3.  The XML message is written to a folder.  
  
## Where to Find This Sample  
 *\<Samples Path>*\Pipelines\CustomPartyResolution\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Assembly information C# source file.|  
|Cleanup.bat|Cleanup batch file.|  
|CustomPartyResolution.sln|Solution file.|  
|CustomPartyResolutionBinding.xml|Binding file.|  
|CustomPartyResolutionPipeline.btp|Pipeline file.|  
|CustomPartyResolutionPipeline.btproj|Pipeline project file.|  
|CustomPartyResolutionPipelineComponent.cs|Pipeline component C# source code.|  
|CustomPartyResolutionPipelineComponent.csproj|Pipeline component Visual Studio project file.|  
|InboundDocumentSchema.xsd|Inbound document schema.|  
|PartyResolutionStream.cs|Party resolution stream C# source code.|  
|RoutingPropertySchema.xsd|Routing property schema file.|  
|SampleInboundDocumentSchema.xml|Inbound document schema file.|  
|SampleInboundDocumentSchema_Party1.xml|Sample data instance.|  
|SampleInboundDocumentSchema_Party2.xml|Sample data instance.|  
|Setup.bat|Build and setup sample pipeline component batch file.|  
  
## Building and Initializing This Sample  
  
#### To build and initialize the Custom Party Resolution sample  
  
1.  In a command window, change directory (**cd**) to the following folder:  
  
     *\<Samples Path>*\Pipelines\CustomPartyResolution\  
  
2.  Run the file Setup.bat, which will perform the following actions:  
  
    -   Creates the input and output directories used in the sample.  
  
    -   Generates a new key file.  
  
    -   Builds and deploys the Custom Party Resolution pipeline component.  
  
    -   Copies the built pipeline component to the *\<Installation Path>*\Pipeline Components directory.  
  
    -   Creates the send and receive ports.  
  
> [!NOTE]
>  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  
  
## Running This Sample  
  
#### To run the Custom Party Resolution sample  
  
1.  Copy to file SampleInboundDocumentSchema_Party1.xml or SampleInboundDocumentSchema_Party2.xml to the \In folder.  
  
2.  The results will appear in the \Out folder with the filename *guid*.xml.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)