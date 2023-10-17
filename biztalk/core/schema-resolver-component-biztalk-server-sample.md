---
description: "Learn more about: Schema Resolver Component (BizTalk Server Sample)"
title: "Schema Resolver Component (BizTalk Server Sample)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Schema Resolver Component (BizTalk Server Sample)
The Schema Resolver Component sample demonstrates how to extend the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] flat file disassembler component.  
  
 The flat file disassembler component normally requires you to define a parsing schema at design time. So if you expect to receive different flat file documents on the same receive location, you typically include several flat file disassemblers in the receive pipeline, one for each schema. At run time, the correct disassembler component is selected using a pipeline probing mechanism. However, this approach is expensive if you have many flat file schemas because probing for every corresponding disassembler component degrades pipeline performance.  
  
## What This Sample Does  
 The Schema Resolver component demonstrates an alternative method of selecting the schema for a flat file disassembler. In this sample, four schemas are defined and the first two characters of a message for each schema are unique. A mapping is defined between the unique first two characters and the corresponding schema. When the input message is given to the Schema Resolver component, it reads the first two characters, determines which schema to use for the corresponding document, saves the schema information on the message context, and then calls into the standard flat file disassembler component. The standard flat file disassembler component reads the schema information from the message context and uses that schema to parse the document.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\Pipelines\SchemaResolverComponent\  
  
 The following table shows the files used in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|SchemaResolverSample.sln|Solution for the BizTalk project that exercises the custom pipeline component.|  
|SchemaResolverSample.btproj|BizTalk project that exercises the custom pipeline component.|  
|SchemaResolverRP.btp|Receive pipeline that contains the custom component.|  
|PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd|Flat file schemas.|  
|POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt|Corresponding flat file document instances.|  
|SchemaResolverFlatFileDasm.sln|Solution for the implementation of the pipeline component.|  
|SchemaResolverFlatFileDasm.csproj|C# project for the implementation of the pipeline component.|  
|SchemaResolverFlatFileDasmComp.cs|Implementation of the pipeline component.|  
|SeekableReadOnlyStream.cs|Implementation of the seekable read-only stream used by component.|  
|VirtualStream.cs|Implementation of the virtual stream used by pipeline component.|  
  
## Building and Initializing This Sample  
 Use the following procedure to build and initialize the Schema Resolver Component sample.  
  
#### To build and initialize this sample  
  
1.  In a command window, change directory (cd) to the following folder:  
  
     *\<Samples Path\>*\Pipelines\SchemaResolverComponent  
  
2.  Run the file Setup.bat, which performs the following actions:  
  
    -   Builds the component.  
  
    -   Copies the component assembly into the BizTalk \Pipeline components folder.  
  
    -   Builds and deploys the sample BizTalk project.  
  
    -   Configures the receive location and send port, and starts them.  
  
    > [!NOTE]
    >  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  
  
## Running This Sample  
 Use the following procedure to run the Schema Resolver Component sample.  
  
#### To run this sample  
  
1.  Drop the POInstance.txt, PRInstance.txt, SOInstance.txt, and SRInstance.txt files into the receive location \<*Installation Path*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In  
  
2.  Observe the four .xml files written to the \<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out folder.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)
