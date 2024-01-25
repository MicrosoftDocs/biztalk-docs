---
description: "Learn more about: EDI Interchange Structural Element"
title: "EDI Interchange Structural Element"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EDI Interchange Structural Element
The interchange is the highest-level structural element of an EDI message. It contains a collection of one or more groups exchanged by two partners. The destination of an interchange must be a single trading partner. Interchanges may contain transaction sets/message of one or more than one type.  
  
 With an interchange, the interchange itself and the groups and transaction sets/messages within it are defined by headers. Segments, data elements, and sub-elements are delimited by separators. Each separator has a default value, but may be defined as a different character for the party. In EDIFACT interchanges, the characters selected for use as separators in the interchange are defined in a separate UNA Interchange Header. In X12 interchanges, separators are defined in the ISA Interchange Header. Note that in X12, the data element separator is the character in the fourth character position, and the data segment terminator is the character in the last character position. The other X12 separators and all the EDIFACT separators are defined by fields, such as the X12 component separator by the ISA16 field and the EDIFACT data element separator by the UNA2 field.  
  
 The interchange includes an envelope that defines the EDI message. The envelope must start with an Interchange Header (ISA in X12 or UNA/UNB in EDIFACT), and it must end with an Interchange Trailer (IEA/UNZ). The Interchange Header includes elements defining the sender and receiver, a date and time, a version number, a control number that matches the header and the trailer, and other information.  
  
 The ISA12 and GS8 fields (for X12 interchanges) and the UNH2 field (for EDIFACT interchanges) contain version information that is required for schema discovery.  
  
 The Interchange Trailer has an element that indicates the number of groups within the interchange.  
  
> [!NOTE]
>  The functional security header, functional assurance header, functional security value segment, and functional security trailer segments are beyond the scope of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2. If an interchange with these segments is received, it will be suspended with an error log indicating that these are unidentified segments.
