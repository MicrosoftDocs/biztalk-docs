---
title: "Common Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4fe48a8e-def0-4a00-aa7f-9a49ae555351
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Common Errors
This topic lists out common error messages you may encounter while creating maps using BizTalk Mapper.  
  
## You receive error event ID 324 when parsing dates  
  
### Problem  
 When you use the Database **Value Extractor** functoid in a map to extract a date field, your document may fail validation against the outbound document definition. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may log a validation error similar to the following in the event log:  
  
 Event Source: BizTalk Server  
  
 Event Category: Document Processing  
  
 Event ID: 324  
  
 Description:  
  
 An error occurred in BizTalk Server.  
  
 Details:  
  
 -----------------------------\-  
  
 The XML document has failed validation for the following reason: Error parsing '10/12/1995' as date datatype.  
  
 Suspended Queue ID: "{A1127909-CA36-4359-B672-7CBA8B60BDAF}"  
  
### Cause  
 The date format (as it is returned from the data source) is not in ISO 8601 format, which is the format required by XML.  
  
### Resolution  
 To resolve this issue, do one of the following:  
  
- Edit your outbound document definition to use a string datatype instead of a date datatype.  
  
- Create a custom [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)]**Script** functoid that will convert the output of the Database **Value Extractor** functoid into the ISO 8601 format.  
  
  For more information, see KB article [278737](http://support.microsoft.com/kb/278737/en-us).  
  
## You receive Internal Compiler Error (0xc0000005 at address 53624FD6) when compiling the maps  
  
### Problem  
 When you compile a single BizTalk project that consists of large schemas, maps, or orchestrations, the compiler may generate an error similar to the following:  
  
 Internal Compiler Error (0xc0000005 at address 53624FD6): likely culprit is 'CODEGEN'.  
  
### Cause  
 The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project. While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation.  
  
### Resolution  
 To resolve this issue, you can separate schemas or maps into different BizTalk projects.  
  
## You receive errors about the Type Name of a BizTalk artifact  
  
### Problem  
 In a BizTalk project, create a map with filename **System.btm** or **Microsoft.btm**. When you build the project, the BizTalk Mapper generates an error similar to any of the following:  
  
-   “The typename ‘SerializableAttribute’ does not exist…”  
  
-   “The typename ‘NonSerializableAttribute’ does not exist…”  
  
-   “The typename ‘SerializableAttributeAttribute’ does not exist…”  
  
-   “The typename ‘XLANs’ does not exist…”  
  
### Cause  
 The **Type Name** in the **Properties** grid should not have any reserved .NET namespaces, such as **System**, **Microsoft**, etc.  
  
### Resolution  
 To resolve this issue, you can follow any of these workarounds:  
  
-   Modify the name of the map to any string which is not a .NET reserved word. By default, the BizTalk project system creates the **Type Name** from the name of the respective artifact.  
  
     For e.g.: Creating a new map with name **Map1.btm** sets the **Type Name** property value to **Map1**. However, renaming an existing BizTalk artifact does not change the **Type Name**.  
  
-   Ensure the filename of any of the artifacts in the BizTalk project is not a .NET reserved namespace.  
  
## You receive errors about the File Name of a BizTalk artifact  
  
### Problem  
 When you build a BizTalk project, the BizTalk Mapper generates an error similar to any of the following:  
  
-   “The File \<filename\> has duplicate values for namespace and type name properties.”  
  
-   “The namespace \<name\> already contains a definition for ‘_’.”  
  
### Cause  
 In the BizTalk project, check for the following:  
  
-   Multiple artifacts have the same filename. For e.g., **Map1.xsd** and**Map1.btm**.  
  
-   The filename comprises of only special characters (**~**, **!**, **@**, etc.).  
  
### Resolution  
 To resolve this issue, you can follow any of these workarounds:  
  
-   Rename the files. Ensure the filenames for all artifacts in the BizTalk project are unique.  
  
-   Ensure Type Name for all artifacts in the BizTalk project are unique.  
  
## Building any C# workflow project with BizTalk Mapper shows a warning regarding version conflict for EnvDTE.dll  
  
### Problem  
 Building any C# workflow project with BizTalk Mapper acitivity always shows the following warning about version conflict for EnvDTE.dll.  
  
 No way to resolve conflict between "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" and "EnvDTE, Version=7.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a". Choosing "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" arbitrarily.  Consider app.config remapping of assembly "EnvDTE, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" from Version "7.0.3300.0" [] to Version "8.0.0.0" [C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll] to solve conflict and get rid of warning. C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9): warning MSB3247: Found conflicts between different versions of the same dependent assembly.  
  
 WorkflowConsoleApplication3 -> C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe  
  
### Cause  
 This happens because of the Microsoft.BizTalk.Mapper.OM.dll which the Mapper activity references.  
  
### Resolution  
 Ignore the warning.  
  
## See Also  
 [Troubleshooting Maps](../core/troubleshooting-maps.md)