---
title: "Message Encodings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, encodings"
  - "messages, code samples"
  - "encoding [messages]"
  - "code samples"
ms.assetid: 360638c0-4094-428f-a7c7-306a5f95a6bf
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Encodings
It is not sufficient to define message semantics in order for HL7 to be useful. Once message content has been determined, the standard has to explain how to represent that content in an actual interface. That is to say, there must be a specified "message encoding". HL7 Version 2 supports two forms of message encoding, a custom delimiter-based encoding, and an XML encoding.  
  
 HL7 chose the original delimiter-based encoding to reduce the size of messages as much as possible. For example, if you compare a data structure in which delimiters separate elements to a structure that positions each element in a fixed set of positions, the delimiter-based structure is far more economical if a) messages do not contain some elements, and b) some elements do not fill all the space allowed. The only overhead in delimiter-based structures is the delimiters themselves.  
  
 The original HL7 encoding defines five delimiters, which each message declares within the MSH segment. These indicate:  
  
- Segments  
  
- Fields  
  
- Components  
  
- Subcomponents  
  
- Repetition (of a field, component, or subcomponent)  
  
  Note that since delimiters are a fundamental aspect of the encoding, you must define them first. One result of this is that there can be no sub-sub-delimiter. At times, this limitation has unfortunate effects upon the design of new data types.  
  
  In June 2003, HL7 published HL7 Version 2, XML Encoding Syntax, Release 1. This standard defines alternate encoding rules for HL7 Version 2.3.1 and 2.4 messages, and provides a mechanism for determining alternate encoding rules for subsequent HL7 2.X versions. In essence, this new standard defines XML element tags for the Version 2.3.1 and V2.4 abstract messages, segments, fields, and data types, and creates rules for defining the tags needed for any new structures created for subsequent versions of the Version 2 standard. The process of defining this standard led to a series of improvements in versions 2.4 and 2.5. This happened because creation of XML tags led to the need to address some longstanding ambiguities in the underlying standard. As a result, a) well-defined message structure codes were created to indicate variations in the abstract messages associated with trigger events, b) repeating groups of segments with an abstract message were formally identified and named, and c) the locally defined data type, CM was replaced with more specific types.  
  
  For example, the following is a simple acknowledgment message using the traditional pipe delimited format:  
  
```  
MSH|^~\&|LAB|767543|ADT|767543|199003141304-0500||ACK^^ACK|XX3657|P|2.4  
MSA|AR|ZZ9380  
ERR|PID^1^16^103&Table value not found&HL70357  
```  
  
 By contrast, the following is the same message represented as an XML document:  
  
```  
<ACK  
xmlns="urn:hl7-org:v2xml"  
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xsi:schemaLocation="urn:hl7-org:v2xml ACK.xsd">  
   <MSH>  
      <MSH.1>|</MSH.1>  
      <MSH.2>^~\&</MSH.2>  
      <MSH.3>  
         <HD.1>LAB</HD.1>  
      </MSH.3>  
      <MSH.4>  
         <HD.1>767543</HD.1>  
      </MSH.4>  
      <MSH.5>  
         <HD.1>ADT</HD.1>  
      </MSH.5>  
      <MSH.6>  
         <HD.1>767543</HD.1>  
      </MSH.6>  
      <MSH.7>  
         <TS.1>199003141304-0500</TS.1>  
      </MSH.7>  
      <MSH.9>  
         <MSG.1>ACK</MSG.1>  
         <MSG.3>ACK</MSG.3>  
      </MSH.9>  
      <MSH.10>XX3657</MSH.10>  
      <MSH.11>  
         <PT.1>P</PT.1>  
      </MSH.11>  
      <MSH.12>  
         <VID.1>2.4</VID.1>  
      </MSH.12>  
   </MSH>  
   <MSA>  
      <MSA.1>AR</MSA.1>  
      <MSA.2>ZZ9380</MSA.2>  
   </MSA>  
   <ERR>  
      <ERR.1>  
         <ELD.1>PID</ELD.1>  
         <ELD.2>1</ELD.2>  
         <ELD.3>16</ELD.3>  
         <ELD.4>  
            <CE.1>103</CE.1>  
            <CE.2>Table value not found</CE.2>  
            <CE.3>HL70357</CE.3>  
         </ELD.4>  
      </ERR.1>  
   </ERR>  
</ACK>  
```  
  
 The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:  
  
-   Support of pipe delimited and XML encoding.  
  
-   Support of translation between XML and pipe delimited encodings.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)