---
title: "Code Page Conversion Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9da679d9-1b62-41e1-928d-653e40df8445
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Code Page Conversion Troubleshooting

## Overview
IBM host systems are designed to utilize Extended Binary Coded Decimal Interchange Code (EBCDIC) when handling character string data types. Windows computers are designed to utilize ANSI or UNICODE. The HIS SNANLS API handles conversion from EBCDIC to and from UNICODE, and UNICODE to and from ANSI. When using the HIS data providers, you may encounter code page conversion errors. This topic contains the following sections:  
  
 [OLE DB Provider for DB2](../core/code-page-conversion-troubleshooting.md#oledb)  
  
 For more information on SNANLS, see [SNA Internationalization Programmer's Reference](./sna-internationalization-programmer-s-reference2.md) in the [Network Integration Programmer's Reference](./network-integration-programmer-s-reference2.md).  
  
 For more information on configuring code page conversion when using the data providers for DB2, see [Data Source Wizard (DB2)](./data-source-wizard-db2-2.md) and [Data Links (DB2)](./data-links-db2-2.md) in [Data Integration (Configuration)](./data-integration-configuration-2.md).  
  
 For more information on configuring code page conversion when using the data providers for host files, see [Data Source Wizard (Host Files)](./data-source-wizard-host-files-2.md).  
  

## See Also  
 [Data Integration (Troubleshooting)](../core/data-integration-troubleshooting-2.md)