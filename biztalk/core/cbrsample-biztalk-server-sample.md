---
title: "CBRSample (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, routing"
  - "messages, filters"
  - "outbound maps"
  - "examples, messages"
  - "messages, routing"
  - "examples, outbound maps"
  - "examples, filters"
  - "messages, examples"
ms.assetid: 8fba494c-9257-4eed-8b6a-867056147c2c
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CBRSample (BizTalk Server Sample)
The CBRSample sample demonstrates how to apply filters and an outbound map to transform and route instance messages based on content.  

## What This Sample Does  
 This sample demonstrates the routing of a message containing name, address, and contact information to one of two folders based on country code. Specifically, this sample does the following:  

1.  Defines a sample message format containing basic information about a person including identity with user ID and full name, address with country code, and phone contact information.  

2.  Promotes the **CountryCode** property in the input document so that it can be used in a port filter to control transformation and routing.  

3.  Transforms the message into a Canadian version when **CountryCode** is equal to 200 or a U.S. version when **CountryCode**is equal to 100. Both transforms pass through all data except middle initial (**Initial**). The Canadian version also maps **State** to **Province** and **ZipCode** to **PinCode**.  

4.  Routes U.S. messages to the US directory and Canadian messages to the CAN directory.  

## How This Sample is Designed and Why  
 The design relies on the default send and receive XML pipelines, property promotion, subscription filters, and outbound maps within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to route messages. The following table shows design elements and their justification.  


|        Design element        |                                                                                                          Reason(s) selected                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Default XML receive pipeline | -   The XMLReceive pipeline supports property promotion; the PassThruReceive pipeline does not.<br />-   The inbound message is already in XML format and does not require processing beyond basic disassembly and party resolution. |
|      Property promotion      |          -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]depends upon property fields to do routing. Distinguished fields are used by orchestrations and cannot be used for routing.           |
|     Subscription filter      |                                                -   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.                                                |
|         Outbound map         |                                                     -   Maps transform data from one format to another. The sample maps an inbound message to either a U.S. or Canadian format.                                                      |
|         XMLTransmit          |                                                         -   Performs basic assembly of outgoing XML messages; the PassThruTransmit pipeline provides no additional support.                                                          |

 This basic pattern can be extended and used for more complex scenarios.  

## Where to Find This Sample  
 This sample is located at <`Samples Path>`\Messaging\CBRSample\\.  

 The following table shows the files in this sample and describes their purpose.  

|File(s)|Description|  
|---------------|-----------------|  
|CBRDataCAN.Xml, CBRDataUS.Xml|Sample input files that conform to the schema defined in the file CBRInputSchema.xsd.|  
|CBRInput2CANMap.btm, CBRInput2USMap.btm|Map files for the Canadian and U.S. format transformations, respectively.|  
|CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd|Schema files for the input format, the Canadian output format, and the U.S. output format, respectively.|  
|CBRPromotedPropertySchema.xsd|Schema file for the promoted property that corresponds to the **CountryCode** element in the XML input files.|  
|CBRSample.btproj, CBRSample.sln|BizTalk project and solution files for this sample.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Internet Information Services (IIS) virtual directories as needed.|  
|Setup.bat|Used to build and initialize this sample.|  

## How to Use This Sample  
 Use this sample as a working example of the actions required to route a message based on content.  

## Building and Initializing This Sample  
 To build and initialize the CBRSample sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.  

#### To build and deploy the BizTalk project for this sample  

1. In a command window, navigate to the following folder:  

    `<Samples Path>` **\Messaging\CBRSample**  

2. Run **Setup.bat**, which performs the following actions:  

   - Creates the input (**In**) and output folders (**US** and **CAN**) for this sample.  

   - Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

   > [!NOTE]
   >  This sample displays the following warning when creating and binding the ports:  
   > 
   >  **Warning: Receive handler not specified for receive location "CBRReceiveLocation"; updating with first receive handler with matching transport type.**  
   > 
   >  You can safely ignore this warning. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  
   > 
   > [!NOTE]
   >  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
   > 
   > [!NOTE]
   >  If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assembly.  
   > 
   > [!NOTE]
   >  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

#### To prepare to configure the receive port and location, and the send ports  

1.  In **Microsoft SQL Management Studio**, select the correct BizTalk Management database.  

    > [!NOTE]
    >  The BizTalk Management database is also referred to as the BizTalk Configuration database.  

#### To configure, enlist, and start the U.S. send port  

1.  In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRUSSendPort**, and then click **Edit**.  

2.  In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **100**.  

3.  In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2USMap**, and then click **OK**. You may have to click the scroll button to bring the map into view.  

#### To configure, enlist, and start the Canadian send port  

1. In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRCANSendPort**, and then click **Edit**.  

2. In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **200**.  

3. In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2CANMap**, and then click **OK**.  

   These steps connect the send port to the receive port. The sample uses promoted properties to route the documents.  

   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is ready now to work with this sample.  

## Running This Sample  
 Use the following procedure to run the CBRSample sample.  

#### To run this sample  

1. Copy the input files, **CBRDataCAN.xml** and **CBRDataUS.xml**, into the following input folder:  

    `<Samples Path>` **\Messaging\CBRSample\In**  

2. Observe how each of these files is transformed and routed to one of the following two output folders based on the value of their **CountryCode** element (100 versus 200):  

   - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] transforms and routes the input file **CBRDataCAN.xml** to the folder:  

      `<Samples Path>` **\Messaging\CBRSample\CAN**  

   - BizTalk Server transforms and routes the input file **CBRDataUS.xml** to the folder:  

      `<Samples Path>` **\Messaging\CBRSample\US**  

## Classes or Methods Used in This Sample  
 None.  

## See Also  
 [Default Pipelines](../core/default-pipelines.md)   
 [How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md)   
 [Messaging (BizTalk Server Samples Folder)](../core/messaging-biztalk-server-samples-folder.md)