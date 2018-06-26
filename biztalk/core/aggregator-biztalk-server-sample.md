---
title: "Aggregator (BizTalk Server Sample) | Microsoft Docs"
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
  - "pipelines, examples"
  - "orchestrations, messages"
  - "examples, pipelines"
  - "messages, correlating to orchestrations"
ms.assetid: eb8121df-4f5b-4f36-8228-4b5ad1abfb4e
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Aggregator (BizTalk Server Sample)
The purpose of this sample is to build a message aggregation functionality using orchestration and pipelines. Specifically we will build an orchestration that:  
  
1.  Receives a set of correlated messages. Messages are correlated based on the destination partner URI information that is extracted from message content.  
  
2.  Aggregates received messages into a single interchange batch by executing an XML send pipeline.  
  
3.  Produces an XML interchange message every minute or as soon as it has enough messages to aggregate.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\Pipelines\Aggregator  
  
 The following table lists the files for this sample.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Aggregator.sln|Visual Studio solution file for the sample.|  
|AggretatorBinding.xml|Binding file for the sample.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC). Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|Setup.bat|Used to build and initialize this sample.|  
|In Aggregate folder:<br /><br /> Aggregate.btproj|BizTalk project for aggregating orchestration.|  
|In Aggregator folder:<br /><br /> Aggregate.odx|Orchestration that collects correlated messages together and then executes send pipeline to assemble them into a single interchange.|  
|In Aggregate folder:<br /><br /> SuspendMessage.odx|Orchestration used for suspending messages that cannot be processed within aggregating orchestration.|  
|In PipelinesAndSchemas folder:<br /><br /> FFReceivePipeline.btp|Receive pipeline with flat file disassembler.|  
|In PipelinesAndSchemas folder:<br /><br /> Instance1.txt, Instance2.txt, Instance3.txt, Instance4.txt|Document instances for the sample. Instance1.txt and Instance2.txt should be added to an interchange for destination partner [http://www.contoso.com](http://www.contoso.com/) while Instance3.txt and Instance4.txt should be added to an interchange for destination partner [http://www.northwind.com](http://www.northwind.com/).|  
|In PipelinesAndSchemas folder:<br /><br /> Invoice.xsd, InvoiceEnvelope.xsd|Document schema and envelope schema for output interchange.|  
|In PipelinesAndSchemas folder:<br /><br /> PipelinesAndSchemas.btproj|BizTalk project for the schemas and pipelines.|  
|In PipelinesAndSchemas folder:<br /><br /> PropertySchema.xsd|Property schema for the sample.|  
|In PipelinesAndSchemas folder:<br /><br /> XMLAggregatingPipeline.btp|Send pipeline that is executed from orchestration to assemble collected messages into an XML interchange.|  
  
## Building and Initializing the Sample  
 Use the following procedure to build and initialize the Aggregator sample.  
  
#### To build and initialize the Aggregator sample  
  
1. In a command window, navigate to the following folder:  
  
    \<Samples Path\>\Pipelines\Aggregator  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Creates the input (In) and output (Out) folders for this sample in the folder:  
  
      \<Samples Path\>\Pipelines\Aggregator  
  
   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.  
  
   - Creates a new application called "Aggregator Sample" and deploys the sample assemblies into it.  
  
   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  
  
   - Enlists and starts orchestration, enables the receive location, and starts the send port.  
  
      If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair is used to sign the resulting assemblies.  
  
3. Before attempting to run this sample, confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process.  
  
    To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  
  
## Running the Sample  
 Use the following procedure to run the Aggregator sample.  
  
#### To run the Aggregator sample  
  
1.  Open Instance1.txt and Instance2.txt files located in PipelinesAndSchemas folder to inspect their content.  
  
     Notice that in both files the DestinationPartnerURI element contains the value http://www.contoso.com. This value will be used to correlate these two messages together so that they can be added to one interchange.  
  
     Similarly Instance3.txt and Instance4.txt files have DestinationPatnerURI element set to http://www.northwind.com.  
  
     These two messages together will be added to a different interchange.  
  
2.  Paste copies of the text files Instance1.txt, Instance2.txt, Instance3.txt, and Instance4.txt into the folder In.  
  
3.  Aggregating orchestrations produce output interchanges as soon as they collect 10 messages or after timeout of 1 minute. Because of that, the files in the Out folder may appear with delay.  
  
     To avoid the timeout, you can paste the four input files four more times, which would trigger the aggregating orchestrations to produce the interchanges.  
  
4.  Observe the XML files created in the folder Out. There should be two files – one per each destination partner URI.  
  
     Open one of the file to inspect its content. The file should contain an XML interchange that consists of an envelope and two XML documents within it.  
  
    > [!NOTE]
    >  The sample implementation may cause "Delivered, not consumed messages" or "Completed with discarded messages" under high load in a convoy scenario. This occurs any time a message routes to a business process that is in the process of ending, or any time unexpected messages arrive into a business process.  
  
## See Also  
 [Pipelines (BizTalk Server Samples Folder)](../core/pipelines-biztalk-server-samples-folder.md)