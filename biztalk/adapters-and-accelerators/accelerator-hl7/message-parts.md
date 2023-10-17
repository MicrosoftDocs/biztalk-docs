---
description: "Learn more about: Message Parts"
title: "Message Parts"

ms.date: "06/08/2017"
ms.prod: biztalk-server




ms.topic: article
helpviewer_keywords: 
  - "messages, segments"
  - "messages, fields"
  - "messages, message parts"
  - "segments, messages"
ms.assetid: 2bb6557e-cd4a-42b7-8bc2-f8b53a59517e
caps.latest.revision: 3



---
# Message Parts
An HL7 message contains the following parts: segments, data fields, components, and optionally subcomponents. HL7 messages have the following hierarchical structure:  
  
 Segment  
  
 Data Field  
  
 Component  
  
 Subcomponent (optional)  
  
 **Segments**  
  
 A segment is a logical grouping of data fields. Segments are at the highest level (depth 1) of the message hierarchy. Each segment has a name that includes a three-character literal value. The following table shows examples of segment names contained by ADT message types.  
  
|Segment code|Description|  
|------------------|-----------------|  
|MSH|Message Header|  
|EVN|Event Type|  
|PID|Patient Information|  
  
 HL7 messages have a *message header* and *body*. The MSH segments define the header of the message and all other types of segments form the body of the message.  
  
 **Data Fields**  
  
 A data field is a string of characters that occur at depth 2 of the message hierarchy. Data types define data fields: Simple and Complex.  
  
 The following example shows the hierarchical message structure of the MSH and EVN segments containing the MSH.1 and EVN.1 data fields:  
  
 MSH  
  
 MSH.1  
  
 EVN  
  
 EVN.1  
  
 **Components and Subcomponents**  
  
 Components and subcomponents further contain the data within data fields. Components and subcomponents can repeat within the same field.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)
