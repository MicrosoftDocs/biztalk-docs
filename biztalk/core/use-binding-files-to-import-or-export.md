---
title: "Use binding files to import or export | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use binding files to import or export

Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can export and import binding files at the **Parties** and **Agreement** levels. For previous BizTalk versions, you export at the application level, as described at: 

* [How to Export Bindings for an EDI-AS2 Solution](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [How to Import Bindings for an EDI-AS2 Solution](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

This topic shows you how to import and exports parties, their profiles, agreements, fallback settings, and more using [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] and BTSTask. 

## Overview

Some of the import and export features include:

* Import parties, business profiles, and agreements from an XML binding file
* Export parties, business profiles, agreements, and EDI fallback settings to an XML binding file
* When importing a binding file, you can chose to not import the parties, or the fallback settings
* When importing at the Parties-level, only the parties and agreements within the binding file are imported
* Export specific parties to the same binding file, and choose to also export all the agreements associated with those parties
* The application import binding wizard lets you choose to import the tracking settings, or exclude the parties.
* BTSTask includes the `ImportParties` and `ExportParties` commands 

## Prerequisites

* You must be logged on with an account that is a member of the** BizTalk Server Administrators** group. See [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  

* You must have added a reference to the **BizTalk EDI Application** from a BizTalk application that will be used as an EDI application. See [Post-configuration steps](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).

## Import or export all the trading partners
1. Open **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, and expand the BizTalk group.
2. Right-click **Parties**, and select **Export**. 

    When you export at the **parties**-level, you are exporting all the trading partners. This also exports everything used by the trading partners, including business profiles, and agreements into an XML file. 

3. Right-click **Parties**, select **Import**, and select the binding XML file. 

      Choose to **Exclude Parties**, or **Exclude EDI Fallback Settings** so they are not imported. Otherwise, everything in the binding file is imported, including the trading partners, business profiles, and agreements.     

### BTSTask example

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

See [ImportParties command](../core/importparties-command.md).

    
## Export individual partners
1. In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, select **Parties**.
2. In the **Parties and business profiles** pane, right-click a party, and select **Export**.

    When you export a specific party, you are given the choice to export all the parties, and all the agreements used by that party. You can uncheck **Export selected parties and all the agreements within the selected parties** to only export the party you select.

3. Select **OK**. 

> [!TIP]
> In the **Parties and business profiles** pane, you can also use the **CTRL** and **Shift** keys to select multiple parties in the list. All of the parties you select export into the same binding file.

### BTSTask example

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

See [ExportParties command](../core/exportparties-command.md).


## Import application binding file

At the application-level, you can import a binding file with EDI and AS2 parties. 

1. In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, expand **Applications**
2. Right-click your application, and select **Import**.
3. **Import Tracking Settings** and **Exclude Parties** options are available. Using these options, you can choose to import any existing tracking settings, or exclude any EDI/AS2 parties within the binding file.

    | Setting | Details |
    |---|---|
    |**Import Tracking Settings** | Imports the tracking settings enabled on the different artifacts within the application, such as track message bodies, and track events. <br/><br/>Enabled by default to ensure backwards-compatibility. |
    | **Exclude Parties**|Does not import parties, profiles, and agreements that existing within the file. <br/><br/>Disabled by default to ensure backwards-compatibility.|

   > [!IMPORTANT]
   > The global tracking settings override **Import Tracking Settings**. So if you've disabled tracking at the global level, any tracking settings are not imported, even if **Import Tracking Settings** is checked.
   > 
   > **BizTalk Settings Dashboard, Group Page** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explains the **Allow import of tracking settings** global setting.

### BTSTask example

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

See [ImportBindings command](../core/importbindings-command.md).

## In this section
To import or export EDI and AS2 binding files on previous BizTalk versions, see: 

* [How to Export Bindings for an EDI-AS2 Solution](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [How to Import Bindings for an EDI-AS2 Solution](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
