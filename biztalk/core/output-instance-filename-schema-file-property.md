---
title: "Output Instance Filename (Schema File Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema file properties, Output Instance Filename property"
  - "Output Instance Filename property [schema file]"
  - "messages, file paths"
ms.assetid: 17a77178-8e84-41bd-a2a2-6ee5d8f0e409
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Output Instance Filename (Schema File Property)
Use the **Output Instance Filename** property to configure the full path of the file to which to which generated instance messages will be written.  
  
## Category  
 General  
  
## Allowed Values  
 Valid, full path file names.  
  
## Default Value  
 None.  
  
## Remarks  
 You can examine and set this property in the **Property Pages** dialog box that is displayed when you right-click a schema file in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer and then click **Properties** on the shortcut menu.  
  
 You can provide this property value in several ways:  
  
-   Type or paste the full path of the file to contain the output instance message into the edit box.  
  
-   Browse to locate the file to contain the output instance message by clicking the ellipsis (**...**) button located to the right of the edit box to open the **Select Output File** dialog box.  
  
 If you do not provide a value for this property, generated output instance messages will be written to your designated temporary folder using a path and filename of the following form:  
  
```  
C:\Documents and Settings\<UserName>\Local Settings\Temp\_SchemaData\<SchemaName>_output.<xml|txt>  
```  
  
## See Also  
 [Schema File Properties](../core/schema-file-properties.md)   
 [Generate Instance Output Type (Schema File Property)](../core/generate-instance-output-type-schema-file-property.md)