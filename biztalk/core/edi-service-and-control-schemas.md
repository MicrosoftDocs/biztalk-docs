---
title: "EDI Service and Control Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4866571b-b12d-446c-8d27-a72fe7e479ef
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Service and Control Schemas
Control schemas are required to process message envelopes (header control schemas) and acknowledgments. These schemas are deployed in Microsoft.BizTalk.Edi.BaseArtifacts.dll by the setup program. These schemas do not have to be added to BizTalk projects because they are deployed in BaseArtifacts.dll. You need to add a reference to the BaseArtifacts.dll assembly to the project containing your schemas for these schemas to be used.  

## Envelope Service Schemas  
 The service schemas X12ServiceSchema and EdifactServiceSchema are used to validate the interchange, group, and transaction set headers and trailers in the envelope of an EDI interchange. This is true for all EDI interchanges: an unbatched interchange, a batched interchange to be split, or a batched interchange to be preserved. The namespaces for these schemas are http://schemas.microsoft.com/Edi/X12ServiceSchema and http://schemas.microsoft.com/Edi/EdifactServiceSchema.  

 When the EDI interchange is a preserved batch interchange, the batch schemas X12_BatchSchema and Edifact_BatchSchema are used by the BizTalk runtime, in addition to the service schemas. For more information, see [EDI Batch Schemas](../core/edi-batch-schemas.md).  

 You can customize ID field enumerations in these schemas. No other modifications are allowed. For more information, see [Customizing Enumerations in the Envelope Schema](../core/customizing-enumerations-in-the-envelope-schema.md).  

## Acknowledgment Control Schemas  
 The EDI receive pipeline uses acknowledgment schemas to generate acknowledgments to be sent and the EDI send pipeline uses them to process received acknowledgments. These schemas include the 997 functional acknowledgment schema and the TA1 interchange acknowledgment schema for X12 encoding, and the CONTRL schema for EDIFACT encoding, as shown in the following table. You cannot modify these schemas.  


|      ACK       |     Schema Name      |             Target Namespace             |                               Root                                |
|----------------|----------------------|------------------------------------------|-------------------------------------------------------------------|
|    X12 TA1     |    X12_TA1Schema     |   http://schemas.microsoft.com/Edi/X12   |                   TA1<br /><br /> X12_TA1_Root                    |
|    X12 997     |    X12_997Schema     |   http://schemas.microsoft.com/Edi/X12   |            ST<br /><br /> SE<br /><br /> X12_997_Root             |
| EDIFACT CONTRL | Edifact_ContrlSchema | http://schemas.microsoft.com/Edi/Edifact | Efact_Contrl_Root<br /><br /> UCD<br /><br /> UCM<br /><br /> UCS |

 For X12 encoding, the 997 functional acknowledgment schema defines the interchange, group, and transaction set/message headers and trailers used in the envelope of a message, and the AK1, AK2, AK3, AK4, AK5, and AK9 segments that report the result of body validation. The TA1 technical acknowledgment schema defines the interchange header and trailer, and the TA1 acknowledgment segment that reports the result of header validation. The naming convention for these schemas is X12_\<version number\>*997.xsd and X12\\*\<version number\>_TA1.xsd. The target namespace for these schemas is http://schemas.microsoft.com/BizTalk/EDI/X12/2006.  

 EDIFACT supports a two-phased acknowledgment paradigm. The first acknowledgment is an interchange receipt that is constructed using three segments from the CONTRL schema. This technical acknowledgment reports the result of header validation. The second acknowledgment uses the remaining segments of the CONTRL schema. The naming convention for this schema is EFACT_\<Version number\>_CONTRL.xsd. The target namespace for this schema is http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006.  

## See Also  
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)   
 [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)