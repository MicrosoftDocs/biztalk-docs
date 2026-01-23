---
description: "Learn more about: &#39;X&#39; and &#39;Y&#39; Optionality"
title: "&#39;X&#39; and &#39;Y&#39; Optionality"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: concept-article
---
# &#39;X&#39; and &#39;Y&#39; Optionality
The SegmentDataElements table in the HL7 Access database contains several Data Items (fields) that have been set as **Req/Opt = X**, meaning that the HL7 standard does not associate this field with this trigger event, as shown in the following table.  
  
|Segment|Version|Chapter|Data Item|Required/<br /><br /> Optional|Report|Number|HTML Standard|  
|-------------|-------------|-------------|---------------|-----------------------------|------------|------------|-------------------|  
|OBX|2.4|7.4.2.9|00577|X|Y|5|ch07.htm#Heading113|  
|OBX|2.4|7.4.2.8|00576|X||0|ch07.htm#Heading112|  
|OBX|2.4|7.4.2.6|00574|X||0|ch07.htm#Heading107|  
|OBX|2.4|7.4.2.17|00936|X|Y|0|ch07.htm#Heading121|  
  
 Since Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] does not specify trigger events, you decide what the required/optional rules, or optionality should be. Based on local site conditions, you may decide to enforce optionality rules. By default, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provides the 23 fields listed as "X" as optional fields.  
  
> [!NOTE]
>  Value "Y" is an error in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Access database. [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] assumes that all the values of **Y** and **Blank** are optional.  
  
## See Also  
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)
