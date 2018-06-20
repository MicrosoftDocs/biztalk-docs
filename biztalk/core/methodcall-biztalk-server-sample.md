---
title: "MethodCall (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, calling"
  - "examples, orchestrations"
  - "orchestrations, methods"
ms.assetid: 6bdc72da-9478-403a-b706-3089b7374ac7
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MethodCall (BizTalk Server Sample)
The MethodCall sample demonstrates how to call a .NET-based method from a BizTalk Server orchestration.  

## What This Sample Does  
 This sample interacts with a .NET-based method using the following sequence of steps:  

1. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an XML input file from the In folder. This file contains information about an addition or subtraction you want the math library to perform.  

2. The orchestration calls the included math library to perform the addition or subtraction specified in the XML input file.  

3. The appropriate math library method, either **Add** or **Subtract**, performs the requested calculation and packages the result as an XML document.  

4. The orchestration places the resulting .xml file in the Out folder.  

## How This Sample is Designed and Why  
 This sample demonstrates the following functionalities:  

-   Leveraging the promoted properties in an orchestration. The three elements in InputSchema.xsd are promoted as distinguished fields. When the orchestration receives the input message, it gets the values of these three fields and assigns them to the corresponding variables declared in the orchestration.  

-   Using the **Decide** shape to express "if-then-else" logic in an orchestration. After the orchestration assigns the values of distinguished fields to internal variables, it enters the **Decide** shape to check whether an addition or subtraction should be performed. If no operation needs to be performed, the orchestration terminates.  

-   Calling an external assembly from an orchestration. If an addition is to be performed, the orchestration calls an external C# assembly and passes in two parameters to perform the addition. The same procedures apply to a subtraction.  

    > [!NOTE]
    >  You need to install the assembly to the global assembly cache before you can call it from the orchestration; otherwise you will receive an XLANG error during run time.  

-   Using the **Message Assignment** shape to construct the output message.  

-   Debugging the orchestration by putting the following code in the Expression shape:  

    ```  
    System.Diagnostics.Debug.WriteLine(iResult);  
    ```  

     You can also write the result to the event log by using:  

    ```  
    System.Diagnostics.EventLog.WriteEntry("MethodCall SDK Sample Debug", System.String.Format("Result = {0}", iResult);  
    ```  

## Where to Find This Sample  
 \<*Samples Path*\>\Orchestrations\MethodCall\  

 The following table shows the files in this sample and describes their purpose.  


|                                          File(s)                                           |                                                                                           Description                                                                                            |
|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        Cleanup.bat                                         | Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed. |
|                                         Input.xml                                          |                                                                                        Sample input file.                                                                                        |
|                                         Setup.bat                                          |                                                                            Used to build and initialize this sample.                                                                             |
| In the \MathLibrary folder:<br /><br /> AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj |                                                                Project and source files for the math library used by this sample.                                                                |
|       In the \MethodCallSample folder:<br /><br /> InputSchema.xsd, OutputSchema.xsd       |                                                                    Schemas for the input and output .xml files, respectively.                                                                    |
| In the \MethodCallSample folder:<br /><br /> MethodCallSample.btproj, MethodCallSample.sln |                                                                           Project and solution files for this sample.                                                                            |
|          In the \MethodCallSample folder:<br /><br /> MethodCallSampleBinding.xml          |                                                                          Used for automated setup such as port binding.                                                                          |
|             In the \MethodCallSample folder:<br /><br /> MethodCallService.odx             |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that calls the math library to perform the requested calculation.                |

## Building and Initializing This Sample  

#### To build and initialize the MethodCall sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\Orchestrations\MethodCall  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (In) and output (Out) folders for this sample in the MethodCall folder.  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, and deploys the resulting assemblies.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.  

   - Enables the receive location, and starts the send port. Enlists and starts orchestration.  

> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  

## Running This Sample  

#### To run the MethodCall sample  

1.  Paste a copy of the file Input.xml into the In folder.  

2.  Observe the .xml file created in the Out folder. This file contains the result of the requested addition or subtraction calculation. The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.  

3.  You can modify the input file to request different addition or subtraction calculations.  

## Uninstalling This Sample  

#### To uninstall the MethodCall sample  

1. At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*\>\Orchestrations\MethodCall\\.  

2. Run Cleanup.bat.  

## See Also  
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)