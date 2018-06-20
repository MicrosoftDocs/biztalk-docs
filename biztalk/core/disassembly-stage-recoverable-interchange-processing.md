---
title: "Disassembly Stage (Recoverable Interchange Processing) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 552b1e90-f75d-4713-8c7b-155a52819308
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disassembly Stage (Recoverable Interchange Processing)
Interchanges are processed at the disassembly stage in two modes:  
  
-   **Standard mode.** When the disassembler component of a receive pipeline is configured to perform standard disassembly, the messages contained in an interchange are extracted, processed by the receive pipeline, mapped, and published as a transactional unit of work. That is, either the entire interchange and its contained messages are fully processed and published into the MessageBox database, or the interchange is placed in the Suspended queue.  
  
-   **Recoverable mode.** When the disassembler component of a receive pipeline is configured to perform **recoverable interchange processing**, the messages contained in an interchange are extracted independently of each other. Messages that are successfully extracted are propagated further down the receive pipeline. Messages that are identified within an interchange but are not successfully extracted are placed in the Suspended queue.  
  
## Examples  
 The following examples illustrate interchange processing scenarios.  
  
### Example 1  
 In this example, the following pseudo-interchange is submitted on a standard interchange receive location. That is, the disassembler component in the receive pipeline is configured for standard interchange processing.  
  
```  
<Interchange>  
<Document1>...</Document1>  
<Document2 failure=”routing”>...</Document2>  
<Document3>...</Document3>  
<Document4 failure=”pipeline” recoverableError=”true”>...</Document4>  
<Document5>...</Document5>  
</Interchange>  
```  
  
 This interchange contains five messages, all of which the disassembler successfully extracts from the interchange. They are processed as follows:  
  
- The first, second, and third messages propagate through the pipeline and are ready to be published.  
  
- The fourth message fails processing at the disassembling stage in the pipeline. This causes all the messages that have already been processed to roll back and the original interchange message to be suspended as resumable.  
  
  The result of submission is:  
  
- Nothing is published. The original interchange is suspended because in standard interchange processing, any extracted message that fails at any point during or after interchange processing results in all extracted messages being discarded and the original interchange being placed on the Suspended queue as resumable.  
  
### Example 2  
 The example uses the same interchange processing and propagation scenario as the previous example, except that the disassembly stage is configured to do recoverable interchange processing.  
  
 The result of submission is that individual extracted messages are all processed and the original interchange is discarded. The individual messages are processed as follows:  
  
-   The first, second, and third messages propagate through the pipeline and are ready to be published.  
  
-   The fourth message fails disassembly processing (that is, something goes wrong after it is extracted) and is ready to be suspended.  
  
-   The fifth message propagates through the pipeline and is ready to be published.  
  
-   After all messages are extracted from the interchange, messages 1, 2, 3, and 5 are published into the MessageBox database, and message 4 is placed on the Suspended queue. Message 2 is also redirected to the Suspended queue because of a routing failure due to no matching subscriber.  
  
## Configuring Recoverable Interchange Processing  
 Recoverable interchange processing is a property of the disassembler component of a receive pipeline. Not all disassembler components allow you to specify recoverable interchange processing; for example, the native BizTalk Framework disassembler does not. If a disassembler supports recoverable interchange processing, then you specify this behavior in Pipeline Designer within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] when you add the disassembler component to the Disassemble stage of the pipeline being designed. After you drag the selected disassembler onto the Disassemble stage of the pipeline, you set the recoverable interchange processing property of that disassembler component to `true`.  
  
### Party Resolution  
 Messages that are successfully extracted in recoverable interchange processing have their sending party identified according to the party configured for the receive port on which the parent interchange arrived. If party resolution fails for any message extracted from a given interchange, then party resolution is considered to have failed for the entire interchange.  
  
### Restrictions  
  
-   When an interchange fails in the disassembler, the interchange is suspended as resumable. However, if the interchange is administratively resumed, it will fail again because the kinds of errors that cause disassembly failure are solely a result of the interchange content, which stays the same when the interchange is resumed. Such a failed interchange must be modified and resubmitted through a receive location.  
  
-   If a message that was successfully extracted from an interchange subsequently fails to propagate through messaging due to an unmatched subscriber, the message is suspended as resumable. This message can be administratively resumed if the cause of the routing failure is fixed.  
  
-   The disassembler component continues to extract messages from an interchange despite the following errors in disassembler components:  
  
    -   Schema not found  
  
    -   Schema ambiguity not resolved (that is, more than one schema exists for the same message type)  
  
    -   XML validation failed  
  
    -   Flat-file parsing failed  
  
-   The disassembler component does **not** continue to extract messages from an interchange if the following error occurs in disassembler components:  
  
    -   Document data is not well-formed XML—any document properties that would cause System.Xml.XmlReader to fail  
  
## See Also  
 [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
 [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)