---
description: "Learn more about: EDI Segment Structural Element"
title: "EDI Segment Structural Element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EDI Segment Structural Element
The segment contains one or more data elements, and is an intermediate unit of information in the message. Each segment starts with a three-character data segment identifier, and ends with a segment terminator (by default the apostrophe (')). The data elements within the segment are separated by data element separators. The data element separator is by default the plus sign (+). A segment is classified as Mandatory or Optional. Separators for outgoing interchanges can be set in the agreements between two trading partners or as part of fallback trading partner agreement.  
  
## Nesting  
 Segments may be grouped in a hierarchical relationship called **nesting**. There are two distinct type of nesting: explicit and implicit. Within any one interchange only one type of nesting can be used.  
  
-   Explicit nesting uses an explicit indication that the loop is nested. When explicit nesting is used, the first component data element in the segment tag will be the segment code. It will be followed by conditional component data elements indicating both the level and the incidence of repetition of the segment. The number of component data elements used for this purpose depends upon the hierarchical level in which the segment appears in the message structure. If the segment is to appear at level one, the component data element immediately following the segment code will be used. If the segment is to appear at level two, the component data element immediately following the segment code and the next component data element will both be used. If the segment is to appear at level three, the three component data elements following the segment code will be used. Pipelines cannot perform structural verification comparing data to hierarchy.  
  
-   In Implicit nesting, the order of the segments specified in the message structure is strictly followed. The nesting relationship between the segments is implicitly evident and no further indication is required for processing.  
  
## Loops  
 One or more segment can repeat as a **loop** inside a transaction set. There are two distinct types of loops: unbounded and bounded.  
  
### Unbounded Loops  
 An unbounded loop does not have a unique identifying segment to mark the beginning and end of the loop. An unbounded loop repeats according to a count. If the count does not have a value, the loop will repeat twice. Each segment in the loop can occur only once in a specified order.  
  
 The start of an unbounded loop is established by a first data element that is unique. The first element can appear once and only once in each occurrence. Unbounded loops can be nested within loops; if so, the inner unbounded loop cannot start at the same ordinal position as any outer loop and cannot start with the same segment ID as any outer loop. The nested loop cannot contain a segment that is also the beginning segment of any outer loop in the same nesting structure.  
  
### Bounded Loops  
 A bounded loop starts with the predefined segment LS (Loop Start) and ends with the predefined segment LE (Loop End). The optionality of the LS segment must match that of the first segment in the loop. A bounded loop can contain another bounded loop.  
  
> [!NOTE]
>  A bounded loop in X12 and an explicit loop in EDIFACT are equivalent.  
  
 Binding is used in a loop to resolve ambiguity. The requirement designator on the LS/LE segments matches the requirement designator of the first segment of the loop. Binding loosens structural restrictions imposed on the usage of certain commonly repeating segments. Bounded segments have no restrictions with respect to the beginning segment ID. This enables the same segment to start a bounded loop and be used outside of the loop, as in the following example:  
  
```  
AA  
LS  
BB  
CC  
LE  
BB  
```  
  
 Subordinate loops (loops within loops) are allowed. If bounded loops are nested within loops, the inner loop cannot start at the same ordinal position as any outer loop. The inner bounded loop must end before the immediate outer loop.  
  
 Each bounded loop within a transaction set must have a uniquely defined <loop_id> value of one to four uppercase letters or numeric digits. It is recommended that the corresponding LS and LE segments contain the same unique <loop_id> value. The <loop_id> data element will be processed as a “regular” data element and validated for data type, min/max length, optionality, etc. Cross-segment validation (across LS and LE) will not be carried out. BizTalk Server will verify ambiguity resolution via the presence of the LS and LE segment and nothing else. In the case of data-element rule violation, the transaction set is accepted with errors, and BizTalk Server returns AK501=E and the appropriate valuation in AK2/AK3 in the ACK.  
  
 It is also required that pairing of LS/LE segments is enforced. In case of a mismatch, the transaction set is rejected due to an inherent ambiguity resolution issue, and AK501 = E and AK502 = 5 are returned in the Event Viewer and the 997 ACK. When  either or both LS/LE segments are missing, but the transaction set is not ambiguous, the transaction set will be accepted with errors, and AK501=E and AK502 = 5 returned.  
  
 An LS/LE pair can be optional or mandatory. However, unless the pair is contained in a parent loop that is repeatable, the pair can never be repeatable. In either case, both MaxOccurs for an LS/LE pair can be 1, but not greater than 1.This is enforced in schema validation.  
  
 The EDI Disassembler and EDI Assembler handle LS and LE segments. During parsing, the Disassembler created XML nodes for the LS and LE segments, and validates the segments. During serializing, the Assembler creates the LS and LE segments from XML nodes, and validates them. If an expected LS or LE segment is missing, the transaction set is suspended/rejected with an AK501 = E and AK502 = 5. If LS/LE segments are present without corresponding data element, and EDI validation is enabled, the transaction set is accepted with errors and AK501 = E and AK502 = 5 are reported in the Event Viewer and the 997 ACK.
