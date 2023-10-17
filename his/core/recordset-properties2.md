---
description: "Learn more about: Recordset Properties"
title: "Recordset Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15432"
ms.assetid: 092cec85-16ec-475f-aadc-4853b178146f
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Recordset Properties
Use the **Recordset** properties page to set design and host definition properties on a recordset.  
  
## Design Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Name of the recordset. The name can be a maximum of 250 Unicode characters.|  
  
## Host Definition Properties  
  
|Use this|To do this|  
|--------------|----------------|  
|**Column Filler**|Recordset filler. Indicates for each row of data sent or received, the number of bytes of FILLER that precedes each row. FILLER causes an untranslated gap in the buffer. FILLER is not visible on the Automation side.|  
|**Variable Sized Rows**|Recordset variable sized rows. Use this option to indicate that the last data item or group item returned from the host varies from zero to the maximum size specified for the data item. When the last data item is character data, it refers to the number of bytes (TI terminology is "variably sized"). When the last data item is an array, it refers to the number of elements. When the last data item is a recordset, it refers to the number of rows. The last two are called "bounded" in TI terminology. The possible values are:<br /><br /> -   **(none)** (default)<br />-   **Half-word binary (16 bits)**. Indicates that the length specifier for the actual size of a variably sized row will be a half-word binary (16-bit) value. This is the default.<br />-   **Full-word binary (32 bits)**. Indicates that the length specifier for the actual size of a variably sized row will be a full word binary (32-bit) value.<br />-   **Half Word (16 bits) Inclusive**. If the value of the actual size of variably sized rows will include the length specifier (the actual size of the row plus 2 or 4 bytes), select this check box. Verify that this check box is cleared if the value should only specify the actual size of a row itself.<br />-   Full Word (32 bits) Inclusive.|  
  
> [!CAUTION]
>  The properties of a component are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the component to function incorrectly.  
  
## See Also  
 [Recordset Column Properties](../core/recordset-column-properties1.md)   
 [Properties (TI Project)](../core/properties-ti-project-2.md)
