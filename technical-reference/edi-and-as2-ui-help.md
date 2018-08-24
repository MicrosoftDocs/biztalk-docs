---
title: EDI and AS2 UI Help
TOCTitle: EDI and AS2 UI Help
ms:assetid: c1b391e8-da12-4b47-8dde-e7bff3ecf815
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226507(v=BTS.80)
ms:contentKeyID: 51531065
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# EDI and AS2 UI Help

 

This section provides information about user-interface (UI) commands in BizTalk Server EDI and AS2. While most of the user interface information related to EDI and AS2 processing in BizTalk Server such as creating parties, profiles, agreements, and fallback settings is available as part of the procedural content ([Configuring EDI Properties](https://msdn.microsoft.com/en-us/library/bb246069\(v=bts.80\)), [Configuring AS2 Properties](https://msdn.microsoft.com/en-us/library/bb245980\(v=bts.80\)), [Configuring Global or Fallback Agreement Properties](https://msdn.microsoft.com/en-us/library/bb245981\(v=bts.80\)), etc.), information related to the following user interface components is provided in this section.

  - **Batching**. The properties included in this page define how BizTalk Server generates and sends an EDI batch to the party.

  - **Status Reports**. You gain access to these screens from the BizTalk Server Administration Console by clicking the BizTalk Group node, and then clicking one of the links in the Status Reports area of the Group Overview pane.

  - **EDI Design-Time XML Tools**. This section describes the dialog boxes associated with the EDI XML Tools used at design time in Visual Studio..

**Trading Partner Management**

The UI that you use to set fallback settings, party properties, profile properties, and EDI and AS2 agreement properties, is called the Trading Partner Management (TPM) module. The TPM screens are in the **Parties** node of the BizTalk Server Administration Console, as described above.


> [!NOTE]
> <P>TPM does not support the use of double-byte character set (DBCS) characters.</P>




> [!NOTE]
> <P>If you change a party or global property in TPM, the properties will be available to the BizTalk Runtime after the cache refreshes every fifteen minutes or after a restart of the BizTalk Service.</P>



## In This Section

  - [Batches Properties Page](batches-properties-page.md)

  - [EDI-AS2 Status Reports UI](edi-as2-status-reports-ui.md)

  - [EDI Design-Time XML Tools UI Help](edi-design-time-xml-tools-ui-help.md)

