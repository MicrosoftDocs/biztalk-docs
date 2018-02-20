---
title: "Subcategories for Invokable TPs (CPI-C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2edf7ee-e481-4d66-b513-29231aeade51
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Subcategories for Invokable TPs (CPI-C)
The following table shows subcategories for invokable transaction programs (TPs).  
  
|Queued<br /><br /> or nonqueued|Application<br /><br /> or service|Starting method|  
|-----------------------------|--------------------------------|---------------------|  
|Queued|Running as an application or a service|Autostarted or operator-started|  
|Nonqueued|Running as an application|Autostarted|  
  
 The concept of a TP running as a service or running as an application is distinct from a service TP or an application TP. Service TP and application TP are SNA terms that describe how a TP is used: either as a supportive service program for other Common Programming Interface for Communications (CPI-C) programs, or directly by a user, as an application. For detailed information about services in Windows, see the Windows documentation.  
  
 To write an autostarted TP so it runs under Windows as a service and also runs in a nonqueued way, write a multithreaded program with an [Accept_Conversation](./accept-conversation-cpi-c-2.md) always outstanding. For more information, see [Invokable TPs](../core/invokable-tps-cpi-c-2.md).  
  
 To run an autostarted TP as an application under Windows make sure the TPSTART program is always started before the TP. 