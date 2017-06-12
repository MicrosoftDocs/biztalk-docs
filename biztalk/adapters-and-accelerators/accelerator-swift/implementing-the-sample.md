---
title: "Implementing the Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd788fd3-b070-40d5-a3d3-ac8e5208cc47
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing the Sample
To implement the sample, proceed as follows:  
  
1.  Create a new folder for SWIFT schemas (\<DocumentSchemaLocation> in the utility syntax). All schemas for which you are going to create/modify the InfoPath forms must be located in this folder when you execute the utility.  
  
2.  If you are generating InfoPath forms for MT messages then copy **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** from **\<drive :> \Program Files\Microsoft BizTalk Accelerator for SWIFT \<Message Pack Version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<Message Pack Version>\Base Schemas** into the folder that you created for SWIFT schemas.  
  
3.  Copy all schemas for which you are going to create InfoPath forms into the folder that you created for SWIFT schemas in Step 1.  
  
4.  Create or designate a folder to hold the created InfoPath form template solution files (\<DestinationFolderPath> in the utility syntax). If you do not create the output folder, the utility will create the same with path and name that you pass on the command line.  
  
5.  [Optional]-  Create a text file \<NameOfFileContainingSchemaList> that lists the message types for messages for which the InfoPath form is to be generated. For e.g. Message Type can be MT103, MT102 etc. The Message names can directly be passed through the command line instead of creating this text file.  
  
## Syntax of Command usage for FormGenerator.exe  
  
```csharp  
FormGenerator [-b]   [-#] <TemplateFolderPath> [<TemplateFolderPath2>   
   [...<TemplateFolderPath#>]]  
 <DestinationFolderPath>     <DocumentSchemaLocation>  
   { [<SpaceSeparatedDocumentSchemaList>] |   [-f <NameOfFileContainingSchemaList>] }  
  
```  
  
 Where:  
  
-   -b: If specified, forms will be compiled after creation.  
  
-   TemplateFolderPath: the folder containing the template files used to create the InfoPath solution  
  
-   -#: If specified, templates will be looked up in multiple template paths (as many as the integer number # specifies) and in the order specified.  
  
-   DestinationFolderPath: the folder where the forms will be created  
  
-   DocumentSchemaLocation: location of schemas (including base and common schemas for MT messages)  
  
-   SpaceSeparatedDocumentSchemaList: space-separated list of schemas like MT103 MT300.  
  
-   -f: If specified, the schema list needs to be read from a file.  
  
-   NameOfFileContainingSchemaList: name of file containing the list.  
  
    > [!NOTE]
    >  The above command is a generic command for MT, MX and Category 0 messages. Specific commands to generate these types of forms are given in the below sections.