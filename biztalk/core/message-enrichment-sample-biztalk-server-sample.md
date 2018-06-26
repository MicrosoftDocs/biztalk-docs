---
title: "Message Enrichment Sample (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a41ed707-dbdb-46b7-97a6-86fdbc8ad285
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Enrichment Sample (BizTalk Server Sample)
The Message Enrichment sample demonstrates how to append interchange headers to transaction-set messages for X12 and EDIFACT documents.  
  
## What This Sample Does  
 This sample demonstrates how to append UNA, UNB, and UNG headers for EDIFACT, and ISA headers for X12, to transaction sets. Specifically, this sample does the following:  
  
1.  When you drop the test message to the \Message Enrichment\In folder, the receive port picks it up, processes it, and drops it in the MessageBox.  
  
2.  The MessageEnrichmentOrchestration picks the test message up from the MessageBox, because it subscribes to messages based on a filter expression set on its receive shape.  
  
3.  The orchestration reads the interchange headers from the context properties of the message.  
  
    > [!NOTE]
    >  UNA and UNG headers are optional in an EDIFACT message, so can be missing in the context properties of a message.  
  
4.  The orchestration writes both the interchange headers and the message body into a single new message.  
  
5.  The orchestration promotes additional properties that are set in the ReceivePortNameCorrelationType correlation type onto the message. These allow users of the orchestration to select a list of the properties they need for their subscription. These properties are written in a construct message shape. Not all context properties that were written to the original message are written to the new message.  
  
6.  The orchestration drops the new message into the MessageBox.  
  
7.  The send port picks up the new message and sends it via the FILE adapter to the \Message Enrichment\Out folder.  
  
## Where to Find This Sample  
 This sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message Enrichment.  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Undeploys the example scenario. In order for it to succeed there must be no active instances of the orchestration. Otherwise, it will fail.|  
|MessageEnrichment.sln|Contains the MessageEnrichment and MessageEnrichmentLibrary projects.|  
|Setup.bat|Deploys an example scenario that consists of a receive port, send port, and orchestration.|  
|EDIFACT_example.edi|An input EDIFACT message.|  
|X12_example.edi|An input X12 message.|  
|MessageEnrichment.btproj|The project containing the MessageEnrichment orchestrations and schemas.|  
|MessageEnrichmentBindings.xml|The file containing bindings for the orchestration, the ports, and the parties.|  
|MessageEnrichmentOrchestration.odx|The orchestration that appends the headers to the message.|  
|MessageEnrichmentOrchestration.odx.cs|The orchestration code that appends the headers to the message.|  
|EFACT_D98B_APERAK.xsd|The EDIFACT schema for the input message.|  
|Enriched_EFACT_D98B_APERAK.xsd|The EDIFACT schema for the output message.|  
|X12_00401_864.xsd|The X12 schema for the input message.|  
|Enriched_X12_00401_864.xsd|The X12 schema for the output message.|  
|Headers.xsd|The schemas for the headers added to the input messages.|  
|MessageEnrichmentLibrary.csproj|The project containing the Headers.cs, OrchestrationUtilities.cs, and ParseHeaders.cs files.|  
|Headers.cs|Includes classes representing headers data.|  
|OrchestrationUtilities.cs|Includes utility methods used by orchestration.|  
|ParseHeaders.cs|Includes the default values for UNA that are used in the new messages. These values are taken from the SerializeEDIFACTHeaders method in ParseHeaders.cs.|  
  
## How to Use This Sample  
 Use this sample as a working example of the actions required to append interchange headers to EDI transaction-set messages.  
  
## Building and Initializing This Sample  
 To build and initialize the Message Enrichment sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.  
  
#### To build and deploy the BizTalk project for this sample  
  
1. Using Notepad.Exe, open [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\  
   MessageEnrichment\properties\AssemblyInfo.cs and add the following line at the bottom of the file:  
  
   ```  
   [assembly: Microsoft.XLANGs.BaseTypes.BizTalkAssembly(typeof(Microsoft.BizTalk.XLANGs.BTXEngine.BTXService))]  
   ```  
  
2. Save the modified AssemblyInfo.cs file and then exit Notepad.  
  
3. In a command window, move to the following folder:  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message Enrichment  
  
4. Run **Setup.bat**, which performs the following actions:  
  
   -   Creates the receive (**in**) and send (**out**) folders for this sample in the \MessageEnrichment folder.  
  
   -   Writes a key pair to MessageEnrichmentLibrary\testkey.snk  
  
   -   Builds and deploys the MessageEnrichmentLibrary.btproj project.  
  
   -   Builds and deploys the MessageEnrichment.btproj project.  
  
   -   Reads binding information in MessageEnrichmentBindings.xml.  
  
       > [!NOTE]
       >  The binding for this project requires that the BizTalk host is marked as Authentication Trusted.  In order to use this with a host that is not trusted, modify the MessageEnrichmentBindings.xml and change the HostTrusted=”true” entries to HostTrusted=”false”.  
  
   -   Updates orchestration bindings.  
  
   -   Updates send ports, send port groups, and receive ports.  
  
   -   Updates parties and enlistments.  
  
   -   Starts the send port.  
  
   -   Enables the receive location.  
  
   -   Enlists and starts the orchestration.  
  
   BizTalk Server is ready now to work with this sample.  
  
## Running This Sample  
 Use the following procedure to run the Message Enrichment sample.  
  
#### To run this sample  
  
1.  Copy the EDIFACT_examples.edi file from the \MessageEnrichment\Instances folder into the \MessageEnrichment\In folder.  
  
2.  Verify that the EDIFACT_examples.edi files disappears from the \MessageEnrichment\In folder, and appears in the \MessageEnrichment\Out folder.  
  
3.  Open the file in the \MessageEnrichment\Out folder. Verify that it is an XML representation of the EDIFACT_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the EDIFACT_examples.edi file, with the exception that the output file has EDIFACT UNA, UNB, and UNG headers.  
  
4.  Repeat steps 1 and 2 with the X12_examples.edi file from the \MessageEnrichment\Instances folder.  
  
5.  Open the new file in the \MessageEnrichment\Out folder. Verify that it is an XML representation of the X12_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the X12_examples.edi file, with the exception that the output file has X12 ISA headers.  
  
## Classes or Methods Used in This Sample  
 None  
  
## See Also  
 [EDI and AS2 (BizTalk Server Samples Folder)](../core/edi-and-as2-biztalk-server-samples-folder.md)