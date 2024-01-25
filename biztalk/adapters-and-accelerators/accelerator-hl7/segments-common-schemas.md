---
description: "Learn more about: Segments Common Schemas"
title: "Segments Common Schemas"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Segments Common Schemas
The **segments_\<*version*\>.xsd** file includes datatypes_\<*version*\>.xsd and contains the definition of all the segments related to the HL7 version. Each message schema uses segments_\<*version*\>.xsd. HL7 message definitions are under each subfolder and include segments_\<*version*\>.xsd. The SegmentDataElements and DataElements Access database tables generate the segments_\<*version*\>.xsd file, which includes a pointer to the Fields.xsd schema file for all data types. The schema file name format is:  
  
```  
  
<xxx>_<nnn>_<vaa>_GLO_DEF.xsd  
```  
  
 Where *xxx* is the message type, *nnn* is the trigger event, *vaa* is the version number, GLO indicates globalize, and DEF indicates default. The schema file *\<xxx\>*<em>*\<nnn\>*\\</em>*\<vaa\>*\_*\<glo\>*\_*\<def\>*.xsdis generated from the EventMessageTypeSegments and SegmentDataElements Access database tables and includes a pointer to the Segments\_\<*version*\>.xsd schema file.  
  
## See Also  
 [HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)
