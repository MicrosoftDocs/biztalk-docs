---
title: "HelloWorld (BizTalk Server Sample) | Microsoft Docs"
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
  - "orchestrations, messages"
ms.assetid: 4416029a-ca76-45a4-b66c-b44cb71ded58
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HelloWorld (BizTalk Server Sample)
The HelloWorld sample demonstrates how to use BizTalk orchestrations to convert an XML message (a purchase order) into a related, but distinct, type of message (an invoice).  
  
## What This Sample Does  
 This sample configures the **In** folder as a receive location. When you place a file, such as the sample file **SamplePOInput.xml**, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message using the following steps:  
  
1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retrieves the XML purchase order message from the receive location folder.  
  
2. The orchestration uses the map file to create an XML invoice from the XML purchase order.  
  
3. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] places the resulting XML invoice message into the send adapter **Out** folder.  
  
## How This Sample is Designed and Why  
 In an intercompany message-exchange scenario, it is often necessary to convert inbound messages received from trading partners into a format that internal applications can recognize. This sample uses a **Receive** shape, a **Transform** shape, and a **Send** shape to achieve this result. The **Transform** shape plays the important role in this sample because it is where the message format conversion occurs. You drag a **Transform** shape into your orchestration and configure the source message, map name, and destination message for it. During run time, the source message is mapped to the destination message by using the map you designated.  
  
 For more information about the **Transform** shape, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md). For more information about building a map, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Orchestrations\HelloWorld\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|HelloOrchestration.odx|Orchestration that coordinates the conversion of the purchase order into an invoice.|  
|HelloWorld.btproj, HelloWorld.sln|Project and solution files for this sample.|  
|HelloWorldBinding.xml|Used for automated setup such as port binding.|  
|InvoiceSchema.xsd, POSchema.xsd|Schemas for the invoice and purchase order messages, respectively.|  
|POToInvoice.btm|Map for converting the purchase order to an invoice.|  
|SamplePOInput.xml|Sample input file.|  
|Setup.bat|Used to build and initialize this sample.|  
  
## Building and Initializing This Sample  
  
#### To build and initialize the HelloWorld sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Orchestrations\HelloWorld  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Creates the input (In) and output (Out) folders for this sample in the following folder:  
  
      \<*Samples Path*\>\Orchestrations\HelloWorld  
  
   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  
  
   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.  
  
   - Enables the receive location, and starts the send port. Enlists and starts orchestration.  
  
> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample. You can confirm this by viewing your event logs.  
  
## Running This Sample  
  
#### To run the HelloWorld sample  
  
1.  Paste a copy of the file SamplePOInput.xml into the **In** folder.  
  
2.  Observe the .xml file created in the **Out** folder. This file contains the XML invoice constructed from the input file SamplePOInput.xml. The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.  
  
## Uninstalling This Sample  
  
#### To uninstall the HelloWorld sample  
  
1.  In a command window, navigate to the following folder:  
  
     \<*Samples Path*\>\Orchestrations\HelloWorld\  
  
2.  Run Cleanup.bat.  
  
## See Also  
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)