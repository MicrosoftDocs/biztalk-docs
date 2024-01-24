---
description: "Learn more about: Alerts Used by Applications and NVAlert"
title: "Alerts Used by Applications and NVAlert2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Alerts Used by Applications and NVAlert
Application programs and the NVAlert service can generate alerts using the Common Service Verb (CSV) **TRANSFER_MS_DATA**. An application or service can supply subvectors, which are required to build an NMVT, or it can supply the complete NMVT. In both cases, the completed NMVT is logged locally, and may also be sent on the connection designated for NetView if the connection is configured and active. An application or service can also supply user-defined alert data, in which case the data is logged locally but cannot be sent.  
  
 This section contains:  
  
-   [Format for Alerts Used by Applications and NVAlert](../core/format-for-alerts-used-by-applications-and-nvalert1.md)
