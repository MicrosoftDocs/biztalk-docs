---
title: "SNA National Language Support Programmer&#39;s Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b7284ef-7fa7-42a4-b501-ce89d0f9e627
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
---
# SNA National Language Support Programmer&#39;s Guide
The SNA National Language Support (SNANLS) API standardizes the way in which national languages and locales are supported. SNANLS handles string conversion necessary for supporting a wide range of host and code pages. Components such as the Host Print service, data providers and Transaction Integrator use SNANLS API to convert strings from EBCDIC to ANSI and from ANSI to EBCDIC.  
  
 The SNANLS API is the standard means to convert strings in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. SNANLS presents a single interface to applications that need strings converted from one code page to another. These conversions may be EBCDIC-to-ANSI, ANSI-to-EBCDIC, EBCDIC-to-OEM code pages, OEM-to-EBCDIC, EBCDIC-to-ISO code pages, and ISO-to-EBCDIC. Additionally, SNANLS supports the broadest possible range of host and PC code page conversions.  
  
 SNANLS provides a uniform interface for programmers, hiding the details and difficulties of string conversion. SNANLS supports both SBCS and DBCS conversions. Two other lower-level APIs handle the actual string conversion. For SBCS conversions, SNANLS uses the system-provided Windows NLS API that is resident on Windows.  
  
 For DBCS conversions, SNANLS uses the **TrnsDT** API. The **TrnsDT** API is installed with Host Integration Server.  
  
 For Arabic and Hebrew bi-directional layout conversion, SNANLS uses the TrnsBiDi API. The TrnsBiDi API is installed with Host Integration Server.  
  
## In This Section  
 [National Language Support in Windows](../core/national-language-support-in-windows.md)