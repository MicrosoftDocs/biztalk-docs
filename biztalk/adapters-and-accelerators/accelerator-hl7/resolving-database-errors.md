---
description: "Learn more about: Resolving Database Errors"
title: "Resolving Database Errors"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Resolving Database Errors
In the HL7 Access database that the HL7 organization publishes, DataItems and TableValues are two tables linked by table_id and hl7_version. The following database cross-query shows that some data items refer to a table_id, which has no values listed in the table:  
  
```  
select distinct d.table_id, d.hl7_version, t.table_item from DataElements as d left join TableValues as t on   
   d.table_id = t.table_id and d.hl7_version = t.hl7_version where d.table_id <>0 order by d.table_id  
```  
  
 If the HL7 Access database has missing enumeration values, you must cross check the values manually with the HL7 specifications and use those values in your schema. One way to deal with this situation is to add an enumeration list to the schema. To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
## See Also  
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)
