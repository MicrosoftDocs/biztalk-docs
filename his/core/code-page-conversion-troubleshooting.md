---
title: "Code Page Conversion Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9da679d9-1b62-41e1-928d-653e40df8445
caps.latest.revision: 6
ms.author: "v-mlynd"
---
# Code Page Conversion Troubleshooting
IBM host systems are designed to utilize Extended Binary Coded Decimal Interchange Code (EBCDIC) when handling character string data types. Windows computers are designed to utilize ANSI or UNICODE. The HIS SNANLS API handles conversion from EBCDIC to and from UNICODE, and UNICODE to and from ANSI. When using the HIS data providers, you may encounter code page conversion errors. This topic contains the following sections:  
  
 [OLE DB Provider for DB2](../core/code-page-conversion-troubleshooting.md#oledb)  
  
 For more information on SNANLS, see [SNA Internationalization Programmer's Reference](../Topic/SNA%20Internationalization%20Programmer's%20Reference1.md) in the [Network Integration Programmer's Reference](../Topic/Network%20Integration%20Programmer's%20Reference1.md).  
  
 For more information on configuring code page conversion when using the data providers for DB2, see [Data Source Wizard (DB2)](../Topic/Data%20Source%20Wizard%20\(DB2\)1.md) and [Data Links (DB2)](../Topic/Data%20Links%20\(DB2\)1.md) in [Data Integration (Configuration)](../Topic/Data%20Integration%20\(Configuration\)1.md).  
  
 For more information on configuring code page conversion when using the data providers for host files, see [Data Source Wizard (Host Files)](../Topic/Data%20Source%20Wizard%20\(Host%20Files\)1.md) and [Data Links (Host Files)](../Topic/Data%20Links%20\(Host%20Files\).md) in [Data Integration (Configuration)](../Topic/Data%20Integration%20\(Configuration\)1.md).  
  
##  <a name="oledb"></a> OLE DB Provider for DB2  
  
## See Also  
 [Data Integration (Troubleshooting)](../core/data-integration-troubleshooting.md)