---
title: "Extending Mapper (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Mapper, examples"
  - "XML tools"
  - "BizTalk Mapper, extending"
  - "examples, BizTalk Mapper"
  - "examples, XML tools"
ms.assetid: 6010a13f-b715-4766-ad91-5aa9b98589e3
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extending Mapper (BizTalk Server Sample)
The Extending Mapper sample demonstrates how to use and extend BizTalk Mapper. The sample includes several [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] map files (.btm), each of which illustrates different features of BizTalk Mapper.  

## What This Sample Does  
 The Extending Mapper sample uses content-based routing (CBR) and does not use an orchestration. By specifying a filter on the sample send port, it is connected directly to the sample receive port. A map is specified on the send port to be applied to the processed document.  

## Where to Find This Sample  
 *\<Samples Path\>*\XmlTools\ExtendingMapper  

 The following table shows the files in this sample and describes their purpose.  


|                                                                             File(s)                                                                             |                                                         Description                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| MapperClassLibrary\AssemblyInfo.cs, MapperClassLibrary\MapperClassLibrary.csproj, MapperClassLibrary\MapperHelper.cs, MapperClassLibrary\MapperClassLibrary.sln | Microsoft® [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]® project file and Visual C#® source files. |
|                                                                           Cleanup.bat                                                                           |                      Used to undeploy assemblies and remove them from the global assembly cache (GAC).                       |
|                                                                         Destination.xsd                                                                         |                                                         Schema file.                                                         |
|                                                           ExtendingMapper.btproj, ExtendingMapper.sln                                                           |                                     BizTalk project and solution files for this sample.                                      |
|                                                                       ExtendingMapper.xml                                                                       |                                                         Source XML.                                                          |
|                                                                   ExtendingMapperBinding.xml                                                                    |                                                         Binding XML.                                                         |
|                                                                      ExternalAssembly.xml                                                                       |                                                    External assembly XML.                                                    |
|                                                                      OverridingMapXslt.btm                                                                      |                                                          Map file.                                                           |
|                                                                      OverridingMapXslt.xml                                                                      |                                                     Overriding Map XML.                                                      |
|                                                                     OverridingMapXslt.xslt                                                                      |                                                 Overriding Map style sheet.                                                  |
|                                                                Scriptor_CallExternalAssembly.btm                                                                |                                                       Sample map file.                                                       |
|                                                            Scriptor_GlobalVariableInInlineScript.btm                                                            |                                                       Sample map file.                                                       |
|                                                                   Scriptor_InlineScripts.btm                                                                    |                                                       Sample map file.                                                       |
|                                                                     Scriptor_InlineXslt.btm                                                                     |                                                       Sample map file.                                                       |
|                                                         Scriptor_InlineXsltCallingExternalAssembly.btm                                                          |                                                       Sample map file.                                                       |
|                                                                  Scriptor_XsltCalltemplate.btm                                                                  |                                                       Sample map file.                                                       |
|                                                                            Setup.bat                                                                            |                                           Used to build and initialize the sample.                                           |
|                                                                           Source.xsd                                                                            |                                                         Schema file.                                                         |

## Building and Initializing This Sample  
 Use the following procedure to build and initialize the Extending Mapper sample.  

#### To build and initialize this sample  

1. In a command window, change directory (**cd**) to the following folder:  

    *\<Samples Path\>*\XmlTools\ExtendingMapper  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (\In) and output (\Out) folders for this sample.  

   - Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

     If you want to use the Scriptor_CallExternalAssembly.btm or Scriptor_InlineXsltCallingExternalAssembly.btm maps, open ExtendingMapper.sln in Visual Studio and make the following modifications (otherwise go to step 3):  

   1. In Solution Explorer, open Scriptor_CallExternalAssembly.btm.  

   2. On the mapper grid, select the Scripting functoid.  

   3. In the property grid, select the **Script** property, and click the ellipsis (...) button to configure the functoid script.  

   4. In the **Configure Scripting Functoid** dialog box, select the **Script Functoid Configuration**, and specify the following:  


      |      Set this       |                           To this                            |
      |---------------------|--------------------------------------------------------------|
      |   **Script Type**   |                      External assembly                       |
      | **Script Assembly** | Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary |
      |  **Script Class**   |    Microsoft.Samples.BizTalk.ExtendingMapper.MapperHelper    |
      |  **Script Method**  |                           MyConcat                           |


   5. From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**File** menu, choose **Save** to save changes to the map file, and close the solution.  

3. Press any key to continue with Setup.bat.  

   > [!IMPORTANT]
   >  If you want to use Scriptor_InlineXsltCallingExternalAssembly.btm, you must edit the ExternalAssembly.xml file. ExternalAssembly.xml is used by BizTalk to map a mapper extension object registered namespace to a .NET assembly. Because the dependent assembly is referenced by its fully qualified name (including its public key token, which is automatically generated), you must update this value. If you do not want to use Scriptor_InlineXsltCallingExternalAssembly.btm, you do not need to complete steps a through e.  

4. In Windows Explorer, navigate to \<Windows folder\>\assembly\\.  

   1. Right-click **Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary** and select **Properties**.  

   2. Copy the public key token value.  

   3. In a text editor, open *\<Samples Path\>*\XML Tools\ExtendingMapper\ExternalAssembly.xml.  

   4. Select the <strong>AssemblyName="Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=68496d20c737d84b"</strong>attribute, and replace the **PublicKeyToken** value with the public key token value you copied in step c.  

   5. Save and close ExternalAssembly.xml.  

   > [!NOTE]
   >  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  

#### To configure, enlist, and start the send port  

1. Click **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.  

2. In the BizTalk Server Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group [\<servername\>:\<management database\>]**, and click to expand **Applications**.  

3. Click to expand **ExtendingMapperApplication**, and then click **Send Ports**.  

4. In the right pane, right-click **Send Ports**, and then click **Properties**.  

5. In the **ExtendingMapperSP – Send Port Properties** dialog box, click the **Outbound Maps** page.  

    In the **Map** column, select the required map from the drop-down list, and then click **OK**. The maps are described in the following table.  


   |                                 Map to apply Property                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_CallExternalAssembly        |                                                                                                                                                                                                                                                                                                                                       Demonstrates how to call into a function in an external .NET assembly from a **Scripting** functoid in a map, based on the input parameters to this functoid. This helps cleanly separate any processing logic from the map file. This map file uses the assembly MapperClassLibrary.dll that ships with this sample.                                                                                                                                                                                                                                                                                                                                       |
   |           Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineScripts           |                                                                                                                                                                                                                                                                                                                                                                                                                 Demonstrates how to write simple inline scripts inside **Scripting** functoids in a map file using .NET languages such as C#, Visual Basic.NET, and JScript.NET.                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |   Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_GlobalVariableInInlineScript    |                                                                                                                                                                                                                                                                                                                                                                                        Demonstrates how to use global variables in the inline scripts of **Scripting** functoids. Global variables are usually used to maintain state information in a map file across different **Scripting** functoids.                                                                                                                                                                                                                                                                                                                                                                                         |
   |            Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXslt             |                                                                                                                                                                                                                                                                                                                                   Demonstrates how to construct structure in the destination document using raw inline XSLT inside a **Scripting** functoid in the map. You can construct some parts of the destination document using **Scripting** functoids with inline XSLT whenever it is not possible to do that in BizTalk Mapper using other functoids.                                                                                                                                                                                                                                                                                                                                   |
   |         Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_XsltCalltemplate          |                                                                                                                                                                                                                                Demonstrates how to create structure in the destination document using an XSLT Call template inside a **Scripting** functoid in the map. The advantage of an XSLT Call template over inline XSLT is that the call template can accept parameters, so you can create the structure based on input parameters to the **Scripting** functoid. You can construct some parts of the destination document using **Scripting** functoids with inline XSLT whenever it is not possible to do that in BizTalk Mapper using other functoids.                                                                                                                                                                                                                                 |
   | Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXsltCallingExternalAssembly |                                                                                                                                                                                                                           Demonstrates how to call into an external .NET assembly from inside The inline XSLT of a **Scripting** functoid in a map. Explains how you can override the **Custom Extension XML** property of the BizTalk Mapper grid with the custom extension file ExternalAssembly_extxml.xml that contains the details of the external .NET assembly to invoke. You can construct some parts of the destination document using **Scripting** functoids with inline XSLT whenever it is not possible to do that in the Mapper UI using other functoids.                                                                                                                                                                                                                           |
   |             Microsoft.Samples.BizTalk.ExtendingMapper. OverridingMapXslt              | Demonstrates how to completely override the compiled XSLT of the BizTalk Mapper file with a custom XSLT file. You can do this by overriding the **Custom XSL Path**property and optionally the **Custom Extension XML** property of the BizTalk Mapper grid. The custom XSLT file that you provide is included in the compiled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly of the project you want to use at run time. In this case, the contents of the map file (.btm) are ignored. This map file uses OverridingMapXslt.xslt and OverridingMapXslt.xml for the **Custom XSL Path** and **Custom Extension XML** properties, respectively.<br /><br /> You can validate a map file in Solution Explorer. You can then use it as a template file that you can edit and use for the **Custom XSL Path** property of the BizTalk Mapper grid. You can resort to this option whenever it is not possible to produce this XSLT using BizTalk Mapper. |

## Running This Sample  
 Use the following procedure to run the Extending Mapper sample.  

#### To run this sample  

1.  Copy the input file ExtendingMapper.xml into the input folder at *\<Samples Path\>*\XmlTools\ExtendingMapper\In.  

2.  Notice how the file is transformed and routed to the *\<Samples Path\>*\XmlTools\ExtendingMapper\Out folder. The transformation that occurs is based on the map you applied.  

## See Also  
 [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md)