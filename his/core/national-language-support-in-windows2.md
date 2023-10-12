---
description: "Learn more about: National Language Support in Windows"
title: "National Language Support in Windows2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# National Language Support in Windows
National Language Support (NLS) provides a standardized method of supporting multiple international locales, code pages, input methods, sort orders, and number/currency/time/date formats.  
  
 The Windows NLS API provides developers with a way to access system-provided Unicode-to-ANSI and ANSI-to-Unicode conversion services. Windows operating systems include EBCDIC-to-Unicode and Unicode-to-EBCDIC translation tables for all of the popular host code pages.  
  
 The SNANLS API leverages the existing work done to support the NLS API on Windows operating systems. Host Integration Server 2013 takes advantage of these EBCDIC-to-Unicode-to-ANSI and ANSI-to-Unicode-to-EBCDIC code page conversion services.  
  
 Currently, the Windows NLS API only supports SBCS EBCDIC code pages. However, future versions of the NLS API will support DBCS EBCDIC. SNANLS currently uses TrnsDT for DBCS conversions.
