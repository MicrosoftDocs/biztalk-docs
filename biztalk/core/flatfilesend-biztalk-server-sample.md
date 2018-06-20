---
title: "FlatFileSend (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52dd0018-e272-40db-a26a-509d444d7106
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FlatFileSend (BizTalk Server Sample)
The FlatFileSend sample demonstrates how you can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process an XML file into the equivalent flat file.  

## What This Sample Does  
 This sample configures the folder FFInput as a receive location. When you place a file, such as the sample file FlatFileSend_in.xml, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following steps:  

1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reads the message from the input file in the receive location folder FFInput.  

2. The message is passed through an XML receive pipeline.  

3. In the MessageBox database, the message is routed to a FILE send port that has a send pipeline configured with a Flat File Assembler component. The Flat File Assembler component converts the XML message to an equivalent flat file representation using a flat file schema.  

4. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] writes the converted message to a text file in the send adapter folder FFOutput.  

## How This Sample is Designed and Why  
 The sample message dictates much of the basic design in this sample. Flat file messages must be assembled using the Flat File Assembler and a flat file schema within a custom send pipeline. These and other design elements are summarized in the following table.  


|    Design element    |                                                                                                                                                                    Reason(s) selected                                                                                                                                                                    |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Custom send pipeline | -   The custom pipeline uses the Flat File Assembler and a flat file schema to translate the instance messages into flat file format; the Flat File Assembler is not itself a pipeline and cannot be used when configuring a send pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management console. |
|   Flat file schema   |                                      -   Define all of the same record and field characteristics (including structure) as an XML schema and provides a mechanism for defining all of the flat file characteristics that are required to translate an XML instance message into a flat file message (or vice versa).                                      |
| Subscription filter  |                                                                                                          -   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.                                                                                                          |
|      XMLReceive      |                                                                                                        -   Performs processing of inbound XML messages. For this example an XML representation of a purchase order is used as the source message.                                                                                                        |

 These elements are combined to produce a solution that accepts purchase order messages in XML format from the receive location and writes out a flat file purchase order to the send location.  

## Where to Find This Sample  
 *\<Samples Path\>*\Pipelines\AssemblerDisassembler\FlatFileSend  

 The following table shows the files in this sample and describes their purpose.  


|                File(s)                |                                                                                           Description                                                                                            |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              Cleanup.bat              | Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed. |
| FlatFileSend.btproj, FlatFileSend.sln |                                                                           Project and solution files for this sample.                                                                            |
|        FlatFileSendBinding.xml        |                                                                          Used for automated setup such as port binding.                                                                          |
|          FlatFileSend_in.xml          |                                                                                        Sample input file.                                                                                        |
|                PO.xsd                 |                                                                                  Schema for outbound flat file.                                                                                  |
|           SendPipeline.btp            |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send pipeline file with the Flat File Assembler component.                           |
|               Setup.bat               |                                                                            Used to build and initialize this sample.                                                                             |

## How to Use This Sample  
 Use this sample as the basis for your own flat file processing solution. You can extend many of the design elements used in this sample to fit your own requirements.  

## Building and Initializing This Sample  

1. In a command window, navigate to the following folder:  

    *\<Samples Path\>*\Pipelines\AssemblerDisassembler\FlatFileSend  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (FFInput) and output (FFOutput) folders for this sample in the folder:  

      *\<Samples Path\>*\Pipelines\AssemblerDisassembler\FlatFileSend  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

     > [!NOTE]
     >  This sample displays the following warnings when creating and binding the ports: `Warning: Receive handler not specified for receive location "FlatFileSend_RL"; updating with first receive handler with matching transport type. Warning: Host not specified for orchestration "FlatFileSend"; updating with first available host.` You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
> 
> [!NOTE]
>  If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assembly.  
> 
> [!NOTE]
>  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running This Sample  

1.  Put a copy of the file FlatFileSend_in.xml into the folder FFInput.  

2.  Observe the text file created in the folder FFOutput. The name of the text file is based on the message ID GUID. This file contains the flat file equivalent of the XML input file FlatFileSend_in.xml.  

## Classes or Methods Used in This Sample  
 The configuration scripts Setup.bat and Cleanup.bat rely on the following administrative Windows Management Instrumentation (WMI) scripts:  

- Start Send Port\StartSendPort.vbs  

- Enable Receive Location\EnableRecLoc  

- Remove Send Port\RemoveSendPort  

  The setup and cleanup batch files use BTSTask as follows:  

- **BTSTask ImportBindings** to apply the binding file and create the application, ports, and bindings  

- **BTSTask RemoveApp** to remove the FlatFileSendApplication  

## See Also  
- [Flat File Schemas](../core/flat-file-schemas.md)   
- [Default Pipelines](../core/default-pipelines.md)   
- [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
- **WMI Script Samples** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
- [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)   
- [FlatFileReceive (BizTalk Server Sample)](../core/flatfilereceive-biztalk-server-sample.md)
