---
title: "Pipeline Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline tools, XMLAsm.exe"
  - "pipeline tools, FFDasm.exe"
  - "Pipeline.exe"
  - "FFDasm.exe"
  - "pipeline tools, XMLDasm.exe"
  - "pipeline tools"
  - "XMLAsm.exe"
  - "pipeline tools, DSDump.exe"
  - "FFAsm.exe"
  - "pipeline tools, FFAsm.exe"
  - "pipeline tools, how to"
  - "pipeline tools, about pipeline tools"
  - "pipeline tools, Pipeline.exe"
  - "utilities, pipeline tools"
  - "XMLDasm.exe"
ms.assetid: ca4d053a-1473-4d40-8cd0-1ed3a3af988a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pipeline Tools
The pipeline tools supplied with the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Software Development Kit (SDK) enable you to verify that a pipeline is functioning correctly without having to configure the BizTalk Server environment, such as send/receive ports. You can also use the pipeline tools to:  

-   Debug third-party pipeline components outside of the server environment.  

-   Diagnose parsing engine error messages.  

-   Experiment with different schemas without the burden of compiling, deploying, undeploying, and recompiling.  

-   Explore flat file and XML assembler/disassembler behavior.  

-   View disassembler output and discover which message context properties are promoted and their values.  

-   Run send/receive pipelines without disassembler and assembler components (for example, you can view the output of the S/MIME decoder).  

-   Make fine-grained performance measurements of the pipeline alone (rather than the entire messaging subsystem).  

## Location in SDK  
 \<*Installation Path*\>\SDK\Utilities\PipelineTools  

 You use pipeline tools for executing, debugging, and profiling pipelines, and pipeline components (that is, flat file and XML assembler/disassembler components).  

## File Inventory  
 The following table lists the pipeline tools files and describes their purpose.  


|   File(s)    |                                                                                                                                                                                                                                Description                                                                                                                                                                                                                                 |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  DSDump.exe  |                                                Enables you to dump the document schema structure, which is an in-memory lightweight representation of the one or more XSD schemas, with or without flat file annotations. This tool can be helpful when you get parsing engine errors such as $Root$0$3$2 and you need to decode them. Numbers after $ mean 0-based index or records as they appear in the document schema.                                                |
|  FFAsm.exe   |                                                                                                                                     Runs the flat file assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes or assembles a user's XML document(s) into a flat file document.                                                                                                                                      |
|  FFDasm.exe  |                                                                                                                               Runs the flat file disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses or disassembles a user's flat file document into one or more XML documents.                                                                                                                               |
| Pipeline.exe | Runs a send or receive pipeline; accepts one or more input documents and their parts, XSD schemas and related information; and produces an output document after the pipeline runs. Pipeline.exe does not access BizTalk Server databases, so pipelines containing BizTalk Framework assembler and disassembler components that access [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases during execution may not be supported. |
|  XMLAsm.exe  |                                                                                                                                 Runs the XML assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes, assembles, or envelopes a user's XML document(s) into an output XML document.                                                                                                                                  |
| XMLDasm.exe  |                                                                                                                             Runs the XML disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses, disassembles, or un-envelopes a user's XML document into one or more XML documents.                                                                                                                              |

## Usage  
 A more detailed description of each file is provided in the sections that follow.  

### DSDump.exe  
 DSDump.exe enables you to dump the document schema structure, which is an in-memory lightweight representation of one or more XSD schemas, with or without flat file annotations.  

 DSDump.exe (document schema dump tool) supports the following command-line parameter:  

```  
DSDump.exe schemaFileName  
```  

 In case of success, DSDump prints the document schema to the console.  

### FFAsm.exe  
 FFAsm.exe (flat file assembler) supports the following command-line parameters:  

```  
usage: ffasm document... [-dm documentMask...]-bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -c ] [ -d ] [ -sb ] [ -m filenamemask ] [ -en encoding ] [ -v ]  

where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -c                 Display assembled FF message on the console  
  -d                 Demote properties  
  -sb                Set body schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Output message encoding name (e.g. windows-1252) or   
                         code page (e.g. 936)  
  -v                 Verbose mode  

file name macros:  
  %MessageID%        FF message identifier (Guid)  
  %MessagePartID%    FF message part identifier (Guid)  

```  

 For example, if you want to assemble three input XML documents into a single flat file document with a header and property demotion, use the following command:  

```  
FFAsm.exe file_in1.xml file_in2.xml file_in3.xml –hs myHeaderSchema.xsd –bs myBodySchema.xsd -d  
```  

### FFDasm.exe  
 FFDasm.exe (flat file disassembler) supports the following command-line parameters:  

```  
usage: ffdasm document -bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -s ] [ -c ] [ -p ] [ -m filenamemask ] [ -en encoding ] [ -v ]  

where:  
  document           Flat File document  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  encoding           Input message body part encoding name (e.g. windows-1252) or code page (e.g., 396)  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  

file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  

```  

 For example, if you want to disassemble a flat file document that has a header, body, and trailer, and display the results to the console, use the following command:  

```  
FFDasm.exe file_in.txt –hs myHeaderSchema.xsd –bs myBodySchema.xsd –ts myTrailerSchema.xsd –c  
```  

### Pipeline.exe  
 Pipeline.exe (the Pipeline tool) supports the following command-line parameters:  

```  
usage: pipeline ( pipeline[.btp] | -pt pipelineTypeName [ -an assemblyName ] ) -d document... [ -part part... ] [ -s schema[.xsd][:namespace.type]... ] [ -proj project[.btproj] ] [ -p ] [ -c ] [ -t ] [ -m filenamemask ] [ -pm partfilenamemask ] [ -en encoding ] [ -v ]  

where:  
  pipeline                Pipeline file name  
  pipelineTypeName     Compiled pipeline assembly qualified type name (e.g.   
"MyPipelines.ReceivePipeline, MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66" or full name (e.g.   
"MyPipelines.ReceivePipeline") if assembly name is   
specified  
  assemblyName         Compiled pipeline assembly file name (e.g.   
MyPipelines.dll) or name (e.g. "MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66")  
  document             Input document(s)  
  part                 Input document's part  
  schema               Schema file name  
  namespace            Schema namespace (as in BizTalk project system)  
  type                 Schema type (as in BizTalk project system)  
  project              BizTalk project file  
  -p                   Display promoted context properties for receive and   
send pipelines, and promote context properties for   
send pipelines  
  -c                      Display output document on the console  
  -t                      Display elapsed time of components execution  
  filenamemask         Output message file name mask (default is   
Message_%MessageID%.out)  
  partfilenamemask     Output part file name mask (default is   
Part_%MessagePartID%.out)  
  encoding             Output message encoding name (e.g. windows-1252)   
or code page (e.g. 936)  
  -v                   Verbous mode  

note:  
You can specify namespace and type for schemas either using namespace.type notation in schema file reference or by using BizTalk project file.  

file name macros:  
  %MessageID%           Message identifier (Guid)  
  %MessagePartID%       Message part identifier (Guid)  
  %MessageNumber%       Message number  

```  

 For example, if you want to run a receive pipeline from the file ReceivePipeline.btp (which has XML disassembler and XML validator components) using mySchema.xsd and display the results to the console, use the following command:  

```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd:MyProject.MySchema -c  

```  

 \- Or -  

```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd –proj MyProject.btproj -c  

```  

 In the first example, a qualified type name (**MyProject.MySchema**) for the schema is included as a command-line argument. In the second example, the schema is obtained from the specified BizTalk project file.  

 You can also run pipelines from the compiled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project files, as in the following example (the pipeline is referenced by its assembly-qualified type name):  

```  
Pipeline.exe -pt "TestBtsProject.ReceivePipeline, TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  

 In the following example, a pipeline is referenced by its type name and assembly file name separately:  

```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an TestBtsProject.dll -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c   
```  

 The following example shows a pipeline referenced by its assembly name:  

```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an "TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  

 Pipeline.exe runs with whatever credentials you have used to launch it. It does not use the account that normal [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instances run under, so you may not be able to run pipelines that contain components that require database access. Make sure you run Pipeline.exe under an account that has all the required privileges.  

 You should only use Pipeline.exe to verify custom pipelines without third-party custom components. If you use pipeline.exe to verify a custom pipeline with third-party custom components, Pipeline.exe will produce the desired output. However, if you deploy the same custom pipeline with third-party custom components, use the pipeline in a receive or send port, and then use Pipeline.exe to submit a message to the pipeline, the pipeline will fail and BizTalk Server will return an error.  

### XMLAsm.exe  
 XMLAsm.exe  (XML Assembler tool) supports the following command-line parameters:  

```  
usage: xmlasm document...[-dm documentmask...] -ds documentSchema... [ -es envelopeSchema... ] [ -c ] [ -d ] [ -sd ] [ -m filenamemask ] [ -v ]  

where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -c                 Display assembled XML message on the console  
  -d                 Demote properties  
  -sd                Set document schema(s) as design-time property  
  -d                 Demote properties  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  

file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  

```  

 For example, if you want to assemble two input XML documents into a single XML document with an envelope and display the results to the console, use the following command:  

```  
FFAsm.exe file_in1.xml file_in2.xml–es myEnvelopeSchema.xsd –ds myBodySchema.xsd –c  
```  

### XMLDasm.exe  
 XMLDasm.exe supports the following command-line parameters:  

```  
usage: xmldasm document -ds documentSchema... [ -es envelopeSchema... ] [ -s ] [ -c ] [ -p ] [ -sd ] [ -se ] [ -m filenamemask ] [ -en encoding ] [ -v ]  

where:  
  document           XML document  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  -sd                Set document schema(s) as design-time property  
  -se                Set envelope schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Input message body part encoding name (e.g., windows-1252) or code page (e.g., 936)  
  -v                 Verbous mode  

file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  %MessageNumber%    XML message number  

```  

 For example, if you want to disassemble an XML document with two nested envelopes and display the results to the console, use the following command:  

```  
XmlDasm.exe file_in.txt –ds myDocumentSchema.xsd –es myEnvelopeSchema1.xsd –es myEnvelopeSchema2.xsd –c  
```  

## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)