---
title: "Subcategories for Invokable TPs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1582dd28-1d79-4ab8-af3e-153a132cfc1c
caps.latest.revision: 4
---
# Subcategories for Invokable TPs (CPI-C)
The following table shows subcategories for invokable transaction programs (TPs).  
  
|Queued<br /><br /> or nonqueued|Application<br /><br /> or service|Starting method|  
|-----------------------------|--------------------------------|---------------------|  
|Queued|Running as an application or a service|Autostarted or operator-started|  
|Nonqueued|Running as an application|Autostarted|  
  
 The concept of a TP running as a service or running as an application is distinct from a service TP or an application TP. Service TP and application TP are SNA terms that describe how a TP is used: either as a supportive service program for other Common Programming Interface for Communications (CPI-C) programs, or directly by a user, as an application. For detailed information about services in Windows, see the Windows documentation.  
  
 To write an autostarted TP so it runs under Windows as a service and also runs in a nonqueued way, write a multithreaded program with an [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md) always outstanding. For more information, see [Invokable TPs](../HIS2010/invokable-tps-cpi-c-1.md).  
  
 To run an autostarted TP as an application under Windows make sure the TPSTART program is always started before the TP. For more information, see [CPI-C Samples](../HIS2010/cpi-c-samples.md).