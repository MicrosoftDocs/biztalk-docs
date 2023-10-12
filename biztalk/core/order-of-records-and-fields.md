---
description: "Learn more about: Order of Records and Fields"
title: "Order of Records and Fields"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Order of Records and Fields
Extensible Stylesheet Language Transformations (XSLT), as used by BizTalk Mapper, do not guarantee the output order of output elements and attributes. This is because BizTalk Mapper generates XSLT by examining the destination schema structure, and then propagating elements back through the grid pages to extract values from the source schema structure. For example, if you want to create an output file that has the BillTo Address record listed before the ShipTo Address record, you must ensure that the BillTo Address precedes the ShipTo Address record in the destination schema.  
  
> [!IMPORTANT]
>  The order in which elements and attributes appear in an output instance message depends on the order of the records and fields of the corresponding destination schema.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)
