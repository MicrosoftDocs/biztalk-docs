---
title: "WCF-CustomIsolated Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "WCF-CustomIsolated adapters"
ms.assetid: 0b529992-65e4-4543-951f-61644f8315a0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-CustomIsolated Adapter
The WCF-CustomIsolated adapter is an isolated adapter to allow configuring receive locations over the HTTP transport with any binding and behavior settings for Windows Communication Foundation (WCF) that are applicable to [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You can use the WCF-CustomIsolated adapter for scenarios that the standard WCF adapters do not support. The WCF-CustomIsolated adapter also enables you to use the WCF extensibility points in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

 The WCF-CustomIsolated adapter is used for the receive location running in an isolated host. To use the WCF-CustomIsolated adapter, you must use the BizTalk WCF Service Publishing Wizard to create in Microsoft Internet Information Services (IIS) the virtual directory corresponding to this receive location.

## In This Section

-   [What Is the WCF-CustomIsolated Adapter?](../core/what-is-the-wcf-customisolated-adapter.md)

-   [Configuring the WCF-CustomIsolated Adapter](../core/configuring-the-wcf-customisolated-adapter.md)

## See Also
 [Introduction to Extensibility](https://go.microsoft.com/fwlink/?LinkId=82590)