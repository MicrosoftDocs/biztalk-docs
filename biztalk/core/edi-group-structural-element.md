---
title: "EDI Group Structural Element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 100a7118-9c02-474e-8685-9e4bb6f52e81
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Group Structural Element
The group contains one or more transaction sets. An EDIFACT group must contain transaction sets of the same type. An X12 group may contain transaction sets of similar type (based on the transaction set – group (GS01-ST01) mapping) or transaction sets of the same type. The table below lists similar X12 transaction sets (ST01), which can occur together in a single group (GS01).  
  
|GS01|ST01|  
|----------|----------|  
|CF|844|  
|CF|849|  
|DX|894|  
|DX|895|  
|FR|821|  
|FR|827|  
|GC|920|  
|GC|924|  
|GC|925|  
|GC|926|  
|HC|837|  
|HC|837_D|  
|HC|837_I|  
|HC|837_P|  
|IA|110|  
|IA|980|  
|IO|310|  
|IO|312|  
|ME|198|  
|ME|200|  
|ME|201|  
|ME|245|  
|ME|261|  
|ME|262|  
|ME|263|  
|ME|833|  
|ME|872|  
|MG|203|  
|MG|206|  
|MG|259|  
|MG|260|  
|MG|264|  
|MG|266|  
|OG|875|  
|OG|876|  
|PK|196|  
|PK|839|  
|QG|878|  
|QG|879|  
|QG|888|  
|QG|889|  
|QG|896|  
|QO|313|  
|QO|315|  
|RO|300|  
|RO|301|  
|RO|303|  
|RQ|836|  
|RQ|840|  
|RS|869|  
|RS|870|  
|SL|135|  
|SL|139|  
|SO|302|  
|SO|311|  
|SO|317|  
|SO|319|  
|SO|322|  
|SO|323|  
|SO|324|  
|SO|325|  
|SO|326|  
|SO|361|  
|TO|197|  
|TO|199|  
|TO|265|  
|TO|485|  
|TO|486|  
|TP|460|  
|TP|463|  
|TP|466|  
|TP|468|  
|TP|490|  
|TP|492|  
|TP|494|  
|WA|140|  
|WA|141|  
|WA|142|  
|WA|143|  
  
> [!NOTE]
>  A HIPAA 5010 group also allows transaction sets of different versions within a single group.  
  
 If an exception is encountered when processing a transaction set, EDI party properties are used to determine if the entire interchange or only the failing transaction set is suspended.  
  
 A group must start with a Functional Group Header (GS in X12 or UNG in EDIFACT), and it must end with a Functional Group Trailer (GE in X12 or UNE in EDIFACT). The Group Header contains sender and receiver codes, a date and time, a control number that matches the header and trailer, a group identifier that defines the collection of transaction sets that may be included within the functional group, and other information. The Group Trailer has an element that indicates the number of transaction sets within the group.  
  
 A group is optional in an EDIFACT interchange. An EDIFACT interchange can contain multiple transaction sets even if no group is present (the UNG segment is not present). In this case, the transaction sets must all be of the same type, as transaction sets in a single group must be of the same type. For example, APERAK and ORDERS transaction sets could not both be present in a single group or in an interchange that does not have multiple groups.  
  
 A group is required in an X12 interchange.