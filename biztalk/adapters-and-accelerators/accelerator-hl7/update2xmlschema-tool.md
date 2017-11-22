---
title: "Update2XMLSchema Tool | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.XML schemas, Update2XMLSchema tool"
  - "schemas, Update2XMLSchema tool"
  - "Update2XMLSchema tool"
  - "Update2XMLSchema tool, syntax"
ms.assetid: fd861e2f-ebda-427f-bd52-a2f05b7e22da
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update2XMLSchema Tool
The Update2XMLSchema tool enables you to modify HL7 2.XML schemas to work with BizTalk Editor. This is necessary because certain HL7 2.XML schemas do not work correctly within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without modification. After modifying the schemas, the tool places them in the Schemas folder where [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] is installed, for instance, *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\Templates\Schemas.  
  
 You need to update manually some fields of the schemas that result from running the Update2XMLSchema tool. See [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) for a list of those schemas.  
  
## Syntax  
 This tool is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\2XML Utilities. You run this tool at the command prompt with the following command:  
  
```  
Update2XMLSchema /s /v  
```  
  
 The following table lists the parameters to use with this command.  
  
|Parameter|Name|Value|  
|---------------|----------|-----------|  
|*S*|Source|Full path of the original HL7 schemas|  
|*V*|Version|The version of the 2.XML schemas:  either 2.3.1, 2.4, or 2.5|  
  
## Example  
  
-   If you want to modify version 2.3.1 2.XML schemas located in the c:\231XML\v231\xsd directory, you would type the following command at the command prompt:  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## In This Section  
  
-   [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)