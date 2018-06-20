---
title: "Added Headers and Subvectors1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec9e18e4-3375-43d9-a5fd-39f5c765332e
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Added Headers and Subvectors
The following table lists Added Headers and Subvectors.  
  
|NMVT header||  
|-----------------|------|  
|41 03 8D 00 00 00 00 00|NMVT Header|  
  
|Major vector header||  
|-------------------------|------|  
|LL LL|Length of Major Vector|  
|00 00 or 00 25|Alert major vector (for the data type ALERT_SUBVECTORS), or Problem Determination Statistics major vector (for the data type PSTATS_SUBVECTORS)|  
  
|              Product set ID subvector              |                                                                                                        |
|----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
|                       4D 10                        |                                        Product set ID subvector                                        |
|                         00                         |                                              Unused field                                              |
|                       34 11                        |                                          Product ID subvector                                          |
|                         0C                         |                                Product classification: non-IBM software                                |
|                       08 04                        |                                 Software product common level subfield                                 |
|                       F0 F2                        |                                         Version identifier: 02                                         |
|                       F0 F0                        |                                         Release identifier: 00                                         |
|                       F0 F0                        |                                      Modification identifier: 00                                       |
|                       20 06                        |                                 Software product common name subfield                                  |
| C4 C3 C1 61 D4 E2 40 C3 D6 D4 D4 40 E2 C5 D9 E5 D9 | Product name: Microsoft [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] |
|                      00 .. 00                      |                                Name padded with nulls to 30 characters                                 |
|                       09 08                        |                                Software product program number subfield                                |
|                F0 F0 F0 F0 F0 F0 F0                |                                     Product program number: zeros                                      |
|                       16 11                        |                                          Product ID subvector                                          |
|                         03                         |                                    Product classification: hardware                                    |
|                       13 00                        |                                      Hardware product ID subfield                                      |
|                         00                         |                                         Format type: undefined                                         |
|                    *hh*...*hh*                     |                                  Server: Windows-based computer name                                   |
  
|Date/time subvector||  
|--------------------------|------|  
|0A 01|Date/Time Subvector|  
|08 10|Local Date/Time subfield|  
|*hh*|Year  two digits|  
|*hh*|Month|  
|*hh*|Date|  
|*hh*|Hours|  
|*hh*|Minutes|  
|*hh*|Seconds|  
  
## See Also  
 [Format for Alerts Used by Applications and NVAlert](../core/format-for-alerts-used-by-applications-and-nvalert1.md)