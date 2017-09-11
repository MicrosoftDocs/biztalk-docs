---
title: "Known Issues with EDI and AS2 Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c47294f9-f728-4b6b-abe1-578434eb54df
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI and AS2 Performance
This topic describes known issues with the performance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.  
  
## Performance Considerations for EDI and AS2 Status Reporting  
 When you activate EDI or AS2 status reporting, the performance of your system may be affected by the number of messages that status reporting is performed for. When you select the "Store transaction set/payload for reporting" property for either EDI or AS2 processing, the performance of your system may be affected by the size of the messages that status reporting is performed for.  
  
 The tables used in the BAMPrimaryImport database for EDI or AS2 status reporting are optimized. No further optimization is required. You can, however, increase the rate at which data from the BAM primary import database is archived by changing the time window for archiving activity instance data in the BAMPrimaryImport database. For more information, see "Archiving Primary Import Database Data" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
 Transaction set/payload data is stored in the BizTalkDTADb database. For more information about the performance of this database, see "Understanding DTA Tracking Performance Behavior" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
 Performance of your system may also be affected by the degree of status reporting enabled in the configuration of your system. You may be able to improve performance by disabling a specific type of status reporting.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)