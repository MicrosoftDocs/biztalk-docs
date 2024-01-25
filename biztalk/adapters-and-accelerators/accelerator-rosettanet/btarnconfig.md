---
description: "Learn more about: BtarnConfig"
title: "BtarnConfig"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# BtarnConfig
You use the BtarnConfig utility to import configuration data into, or export configuration data from, a Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] environment. This configuration data is the data that you set by using the BTARN Management Console, including process configuration settings, home organizations, partners, and agreements.  

## Location in SDK  
 \<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK  

## Running BtarnConfig  

#### To run BtarnConfig  

1. Open a command prompt.  

2. Move to \<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  

3. At the command prompt, type **BtarnConfig**, type the appropriate switches, and then press ENTER.  

   > [!NOTE]
   >  The following section describes the switches.  

## Syntax for BtarnConfig  
 The following shows the syntax that you use to start this command-line tool:  

### Syntax for Importing Configuration Data  

```  
BTARNCONFIG /IMPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  

### Syntax for Exporting Configuration Data  

```  
BTARNCONFIG /EXPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  

### Syntax Description  
 The following table describes each part of the syntax that the BtarnConfig utility uses.  


|       Syntax       |                                                                                                                          Description                                                                                                                          |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \<*filename*.xml\> | Full path of the file to import into or export from. If you do not provide a path, BTARN assumes that the path is \<*drive*\>\ Program Files (x86)\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK. |
|    **/IMPORT**     |                                                                                          Imports the XML data from \<*filename*.xml\> into the BTARN configuration.                                                                                           |
|    **/EXPORT**     |                                                                                             Exports the BTARN configuration as XML data into \<*filename*.xml\>.                                                                                              |
|       **/H**       |                                                                                                   Imports or exports home-organization configuration data.                                                                                                    |
|       **/P**       |                                                                                                        Imports or exports partner configuration data.                                                                                                         |
|       **/R**       |                                                                                                        Imports or exports process configuration data.                                                                                                         |
|       **/A**       |                                                                                                       Imports or exports agreement configuration data.                                                                                                        |

## Remarks  
 If you do not provide any one of the **/H**, **/P**, **/R**, or **/A** switches, the BtarnConfig utility imports or exports all the data. When you export all the data in one operation, BtarnConfig exports the data into the XML file in the following order: home organizations, partners, process configuration, and agreements.  

 If there is a structural problem with the file that you are importing from, BTARN will detect the error during the schema validation stage, and the operation will fail before any data is imported. If another error occurs, for example, you are trying to import a duplicate artifact or HTTPS is required for the PIP/agreement, then the import operation will fail. However, all the data imported up to that point will remain in the configuration.  

 You must be a BizTalk administrator to import or export configuration data using BtarnConfig. If you are not a BizTalk administrator, some import operations may fail because of access issues. However,  other import operations in the same BtarnConfig command may succeed.  

## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
