---
title: "Generate Schemas Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.editor.schemas.generate"
helpviewer_keywords: 
  - "Generate Schemas dialog box [BizTalk Editor]"
  - "schemas, generating"
  - "BizTalk Editor, Generate Schemas dialog box"
  - "generating, schemas"
ms.assetid: 82747abd-2e73-40e3-9b49-9d8d09505ca1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate Schemas Dialog Box
Use the **Generate Schemas** dialog box to generate an XSD-based BizTalk Server schema from one of the following input sources:  
  
-   A valid XML-data reduced (XDR) schema.  
  
-   A valid document type definition (DTD).  
  
-   A well-formed XML instance message that the XSD schema will describe.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Document type**|Select the type of input file from which the schema will be generated. The drop-down list contains three entries, one for each of the supported input sources.|  
|**Input file / Browse**|Type, paste, or browse for the name of the input file that matches your selection for the type of the input file.|  
  
 The schema generation modules for DTDs and well-formed XML are not loaded by default, as indicated by the string "(Not loaded)" appended to the relevant drop-down list selections. You must run the scripts InstallDTD.vbs and/or InstallWFX.vbs to load the DTD and well-formed XML schema generation modules, respectively. These scripts are in the following folder:  
  
 \<*InstallationPath*>\SDK\Utilities\Schema Generator  
  
## See Also  
 [How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)