---
description: "Learn more about: Sample Message Presentation"
title: "Sample Message Presentation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, SWIFT message block"
  - "SWIFT messages, message block example"
ms.assetid: 3136a7da-658d-4100-bbe5-2186ee8bafd1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Message Presentation
The following table shows an example of the block layout of a SWIFT message.  
  
|Block|Example|  
|-----------|-------------|  
|**Block 1** Basic Header|{1:F01BCITITMMAXXX0012000123}|  
|**Block 2** (I) Application Header Input (to SWIFT)<br /><br /> Or<br /><br /> **Block 2** (O) Application Header Output (from SWIFT)|{2:I103VBOEATWWXXXXN} Or {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3|  
|**Block 3** User Header|{3:{108:BCITITMMA950906}}|  
|**Block 4** Text|{4:\<CRLF\> :20:1234567890\<CRLF\> :23B:CRED\<CRLF\> :32A:010605GBP45000,\<CRLF\> :33B:GBP45000,\<CRLF\> :50K:MASTERS IMPORT\<CRLF\> RUE DES ARBRES 119\<CRLF\> CAMBRAI\<CRLF\> :52A:BNPAFRPPCAM\<CRLF\> :53A:POCIITMM680\<CRLF\> :57A:BCITITMM680\<CRLF\> :59:/P03452032022819 30\<CRLF\> GRAND IMPORT\<CRLF\> PESCARA\<CRLF\> :70:/RFB/INV 5591\<CRLF\> :71A:SHA\<CRLF\> -}|  
|**Block 5** Trailers|{5:{MAC:12345678}{CHK:123456789ABC}}|  
  
## See Also  
 [SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/swift-schemas.md)
