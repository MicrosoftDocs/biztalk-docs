---
title: "Splitting HIPAA Subdocuments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66d9badd-00c6-43a3-807e-0ad313983adc
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Splitting HIPAA Subdocuments
EDI interchanges for HIPAA commonly have multiple child/sub documents within a single transaction set, as bounded by the ST/SE headers. The EDI receive pipeline supports creation of separate HIPAA subdocuments from such an transaction set. This is different from non-HIPAA EDI interchanges, in which a single transaction set is processed as a single message.  
  
## Subdocument Splitting Schemas  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports splitting of the following HIPAA document types through native schemas:  
  
- HIPAA version 4010 documents: 834 Enrollment, 835 Claim Payment and three variants of 837 Claim  
  
- HIPAA version 5010 documents: 276/277 Claim Status – Request and Response, 834 Enrollment and three variants of 837 Claim  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides two versions of schemas for each of these three document types. For each document type, the schema supporting splitting is identified by the ‘Multiple’ tag in the file name. The other schema does not support subdocument splitting.  
  
  In some scenarios, both splitting and non splitting schemas may be required. This will be supported through the use of a custom target namespace for one variant of the schema.  
  
## How Subdocument Splitting Is Enabled  
 The splitting of HIPAA subdocuments is enabled by three annotation entries in the HIPAA schema. The first two are  entries for the schema in the appinfo annotation, which must be set to **yes**:  
  
```  
subdocument_break = "yes" Split_Without_Sibling_Data = "Yes"  
```  
  
 The third annotation entry is located at the appropriate record levels within the HIPAA schema. This property must also be set to **yes**.  
  
```  
subdocument_creation_break = "yes"  
```  
  
 A HIPAA interchange will be split into subdocuments only if the subdocument creation break annotation within the HIPAA schema is set to "yes", and the Inbound batch processing option party property is set to "Split Interchange as Transaction Sets". If the Inbound batch processing option party property is set to preserve the interchange, the EDI disassembler will not split the interchange into subdocuments. In this case, the EDI disassembler will ignore the annotation. No warning will be raised in the event viewer if this occurs.  
  
> [!NOTE]
>  Subdocument creation break annotations cannot be nested. If a schema includes a loop that has a subdocument annotation applied to it, that loop cannot contain another loop that has a subdocument annotation applied to it.  
  
## How Subdocuments are Processed  
 The EDI disassembler in the EDI receive pipeline splits the subdocuments. After the receive pipeline validates the incoming interchange and generates the appropriate acknowledgments, it routes each separate subdocument to the MessageBox. Each subdocument is structurally and syntactically valid; however, business level summaries, transaction set totals, and transaction set control numbers are expected to be out of synchronization. The send pipeline will overwrite the value of the existing segment count in SE01 of each subdocument (which came from the original transaction set) to the count of included segments in the subdocument. The receive pipeline will also reset the transaction set control numbers in each subdocument so that the subdocument do not have duplicate control numbers. This ensures that send-side processing will not fail.  
  
 If a transaction set fails EDI or extended validation during subdocument splitting, the individual failing transaction set is suspended.  
  
 A send port that subscribes to the subdocuments will pick up each subdocument from MessageBox, serialize the XML subdocuments, batch them (if enabled), validate them, and send them. The send pipeline updates the count of segments data element (SE01).  
  
## How Subdocuments Are Split  
 A subdocument creation break annotation is commonly applied to a loop that encompasses one or more elements within a HIPAA schema. Other elements before and after the break loop in the schema are replicated in each of the multiple subdocuments.  
  
 The following table shows an example of subdocument splitting. In this example, the subdocument creation break annotation is set to "yes" for the CC element loop. As a result, the CC elements in the transaction set are separated into separate subdocuments, while the AA, BB, and DD elements in the transaction set are all included in each separate subdocument.  
  
|Schema(min and max occurrences)|Original Instance|Subdocument #1|Subdocument #2|Subdocument #3|  
|---------------------------------------|-----------------------|---------------------|---------------------|---------------------|  
|ST (1,0)|ST|ST|ST|ST|  
|AA (1,1)|AA|AA|AA|AA|  
|BB loop (1,n)<br /><br /> BB1 (1,n)<br /><br /> CC loop (1,n) - subdocument_break = "yes"<br /><br /> CC1 (1,n)<br /><br /> CC2 (0,n)<br /><br /> BB2 (0,n)|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1<br /><br /> BB1\*2<br /><br /> CC1\*2<br /><br /> CC2\*2<br /><br /> BB1\*3<br /><br /> CC1\*3<br /><br /> CC2\*3|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1|BB1*2<br /><br /> CC1\*2<br /><br /> CC2\*2|BB1*3<br /><br /> CC1\*3<br /><br /> CC2\*3|  
|DD (0,n)|DD|DD|DD|DD|  
|SE|SE|SE|SE|SE|