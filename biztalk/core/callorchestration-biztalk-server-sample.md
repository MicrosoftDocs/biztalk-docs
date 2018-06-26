---
title: "CallOrchestration (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "orchestrations, calling"
  - "examples, orchestrations"
ms.assetid: 0c4194f0-c1e2-419a-8a1a-a3c96e8d2667
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CallOrchestration (BizTalk Server Sample)
The CallOrchestration sample demonstrates how to call one BizTalk orchestration from another orchestration.  
  
## What This Sample Does  
 This sample demonstrates one orchestration calling another orchestration using the following sequence of steps:  
  
1.  The primary orchestration receives a purchase order (PO) message.  
  
2.  The primary orchestration calls the secondary orchestration to determine the shipping price for the PO.  
  
3.  The secondary orchestration calculates the requested shipping price and returns it to the primary orchestration.  
  
4.  The primary orchestration updates the PO message with the returned shipping price.  
  
5.  The primary orchestration puts the updated PO message into a folder for your inspection.  
  
## How This Sample is Designed and Why  
 The primary purpose of this sample is to show you how to call an orchestration from within another orchestration. The ability to call orchestrations gives you a way to divide your business processes into reusable components. You can factor your common processes out into separate orchestrations for others to re-use.  
  
 In this sample, the **Call Orchestration** shape in receivePO.odx invokes findShippingPrice.odx and waits for the nested orchestration, findShippingPrice.odx, to calculate and return the shipping price before sending the purchase order. The orchestration findShippingPrice.odx uses the following logic to calculate the shipping price:  
  
```  
If ( weight * shippingRate ) < minShippingPrice Then  
    shippingPrice = minShippingPrice  
Else  
    shippingPrice = weight * shippingRate  
End If  
```  
  
 The sample input PO file, InputPO.xml, specifies a weight of 20, resulting in the output PO message having its shipping price changed from 10 to 20.  
  
> [!NOTE]
>  You cannot call a long-running transaction from an atomic orchestration.  
  
> [!NOTE]
>  The difference between using the **Call Orchestration** shape and the **Start Orchestration** shape is that when calling an orchestration, the caller waits for the nested orchestration to return before continuing. When starting an orchestration from an orchestration, after the caller initiates the action, the caller moves forward to the next step in the process flow. The orchestration that was invoked by the caller runs independently until it finishes the process flow. For more information, see [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md). Also see [How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md).  
  
## Where to Find This Sample  
 \<*Samples Path*\>\Orchestrations\CallOrchestration\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|CallOrchestration.btproj, CallOrchestration.sln|Project and solution files for this sample.|  
|CallOrchestrationBinding.xml|Used for automated setup such as port binding.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.|  
|findShippingPrice.odx|BizTalk orchestration that serves as a secondary orchestration, called from the primary orchestration, receivePO.odx.|  
|InputPO.xml|Sample input PO message that conforms to the schema defined in the file PO.xsd.|  
|PO.xsd|Schema that defines the structure of inbound PO messages such as the sample input file InputPO.xml, and defines property promotion for all three elements in the schema.|  
|PropertySchema.xsd|Property schema file that participates in property promotion for all three elements in the schema PO.xsd.|  
|receivePO.odx|BizTalk orchestration that serves as the primary orchestration in this sample. It retrieves PO messages from the receive folder and then calls the other orchestration, findShippingPrice.odx, to calculate and update the shipping price.|  
|Setup.bat|Used to build and initialize this sample.|  
  
## Building and Initializing This Sample  
  
#### To build and initialize the CallOrchestration sample  
  
1. In a command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Orchestrations\CallOrchestration\  
  
2. Run the file Setup.bat, which performs the following actions:  
  
   - Creates the input (In) and output (Out) folders for this sample in the CallOrchestration folder.  
  
   - Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project, containing both orchestrations, for this sample.  
  
   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  
  
   - Enables the receive location, and starts the send port.  
  
> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
  
## Running This Sample  
  
#### To run the CallOrchestration sample  
  
1.  Put a copy of the file InputPO.xml into the In folder.  
  
2.  Observe the updated XML PO file created in the Out folder. It contains the original PO message, modified to include a shipping cost calculated as explained earlier. The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.  
  
## Uninstalling This Sample  
  
#### To uninstall the CallOrchestration sample  
  
1. In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:  
  
    \<*Samples Path*\>\Orchestrations\CallOrchestration\  
  
2. Run Cleanup.bat.  
  
## See Also  
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)