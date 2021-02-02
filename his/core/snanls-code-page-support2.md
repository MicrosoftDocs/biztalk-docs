---
description: "Learn more about: SNANLS Code Page Support"
title: "SNANLS Code Page Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f3dec40-5306-405c-82bf-ed163266f7a3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SNANLS Code Page Support
The SNA National Language Support (SNANLS) API provides functions for converting single-byte character stream (SBCS) EBCDIC-to-Unicode-to-ANSI and SBCS ANSI-to-Unicode-to-EBCDIC by leveraging the Win32 National Language Support (NLS) API. The Win32 NLS API uses resource files containing NLS conversion tables that are installed on the target computer when Windows is installed or installed by the Setup program for Host Integration Server (the Setup program also adds the required registry entries). The SNANLS DLL is supplied with Host Integration Server.  
  
 SNANLS supports conversions for the following groups of code pages:  
  
-   ANSI code pages  
  
-   ANSI/OEM code pages  
  
-   EBCDIC code pages  
  
-   OEM PC code pages  
  
-   Open Systems code pages  
  
-   ISO code pages  
  
## In This Section  
 [ANSI Code Page Support (SNANLS)](../core/ansi-code-page-support-snanls-2.md)  
  
 [ANSI/OEM Code Page Support (SNANLS)](../core/ansi-oem-code-page-support-snanls-1.md)  
  
 [EBCDIC Code Page Support (SNANLS)](../core/ebcdic-code-page-support-snanls-1.md)  
  
 [ISO Code Page Support (SNANLS)](../core/iso-code-page-support-snanls-1.md)  
  
 [OEM PC Code Page Support (SNANLS)](../core/oem-pc-code-page-support-snanls-1.md)  
  
 [SNANLS Dependencies](../core/snanls-dependencies2.md)
