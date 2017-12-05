---
title: "SNANLS Code Page Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65fa91cc-8f70-4ac9-920a-a246ac6c24ec
caps.latest.revision: 4
---
# SNANLS Code Page Support
The SNA National Language Support (SNANLS) API provides functions for converting single-byte character stream (SBCS) EBCDIC-to-Unicode-to-ANSI and SBCS ANSI-to-Unicode-to-EBCDIC by leveraging the Win32 National Language Support (NLS) API. The Win32 NLS API uses resource files containing NLS conversion tables that are installed on the target computer when Windows is installed or installed by the Setup program for [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] (the Setup program also adds the required registry entries). The SNANLS DLL is supplied with Host Integration Server.  
  
 SNANLS supports conversions for the following groups of code pages:  
  
-   ANSI code pages  
  
-   ANSI/OEM code pages  
  
-   EBCDIC code pages  
  
-   OEM PC code pages  
  
-   Open Systems code pages  
  
-   ISO code pages  
  
## In This Section  
 [ANSI Code Page Support (SNANLS)](../HIS2010/ansi-code-page-support-snanls-1.md)  
  
 [ANSI/OEM Code Page Support (SNANLS)](../HIS2010/ansi-oem-code-page-support-snanls-2.md)  
  
 [EBCDIC Code Page Support (SNANLS)](../HIS2010/ebcdic-code-page-support-snanls-2.md)  
  
 [ISO Code Page Support (SNANLS)](../HIS2010/iso-code-page-support-snanls-2.md)  
  
 [OEM PC Code Page Support (SNANLS)](../HIS2010/oem-pc-code-page-support-snanls-2.md)  
  
 [SNANLS Dependencies](../HIS2010/snanls-dependencies1.md)