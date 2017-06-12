---
title: "EDI and AS2 UI Help | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EDI UI, about EDI UI"
  - "AS2 UI, about AS2 UI"
  - "tools, AS2 UI"
  - "AS2 UI"
  - "tools, EDI UI"
  - "EDI UI"
ms.assetid: c1b391e8-da12-4b47-8dde-e7bff3ecf815
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI and AS2 UI Help
This section provides information about user-interface (UI) commands in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2. While most of the user interface information related to EDI and AS2 processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] such as creating parties, profiles, agreements, and fallback settings is available as part of the procedural content ([Configuring EDI Properties](../core/configuring-edi-properties.md), [Configuring AS2 Properties](../core/configuring-as2-properties.md), [Configuring Global or Fallback Agreement Properties](../core/configuring-global-or-fallback-agreement-properties.md), etc.), information related to the following user interface components is provided in this section.  
  
-   **Batching**. The properties included in this page define how BizTalk Server generates and sends an EDI batch to the party.  
  
-   **Status Reports**. You gain access to these screens from the BizTalk Server Administration Console by clicking the BizTalk Group node, and then clicking one of the links in the Status Reports area of the Group Overview pane.  
  
-   **EDI Design-Time XML Tools**. This section describes the dialog boxes associated with the EDI XML Tools used at design time in Visual Studio..  
  
 **Trading Partner Management**  
  
 The UI that you use to set fallback settings, party properties, profile properties, and EDI and AS2 agreement properties, is called the Trading Partner Management (TPM) module. The TPM screens are in the **Parties** node of the BizTalk Server Administration Console, as described above.  
  
> [!NOTE]
>  TPM does not support the use of double-byte character set (DBCS) characters.  
  
> [!NOTE]
>  If you change a party or global property in TPM, the properties will be available to the BizTalk Runtime after the cache refreshes every fifteen minutes or after a restart of the BizTalk Service.  
  
## In This Section  
  
-   [Batches Properties Page](../core/batches-properties-page.md)  
  
-   [EDI-AS2 Status Reports UI](../core/edi-as2-status-reports-ui.md)  
  
-   [EDI Design-Time XML Tools UI Help](../core/edi-design-time-xml-tools-ui-help.md)