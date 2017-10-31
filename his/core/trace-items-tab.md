---
title: "Trace Items Tab1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "trace_trace_items_tab"
ms.assetid: f0b38532-0fb9-47ba-941c-ff1204d3b7ad
caps.latest.revision: 3
---
# Trace Items Tab
The **Trace Items** tab has several items that must be selected and configured for the Trace application to operate properly.  
  
## List of Trace Items  
 The following components can be configured for tracing.  
  
-   SNA applications  
  
-   SNA Manager Client  
  
-   SNA Manager Agent (MngAgent)  
  
-   DB2 Network Library  
  
## Trace Items - Properties  
 **Properties** displays the **Trace Properties Sheet** that contains an **Internal Trace**, **Message Trace**, **API Trace** or the **TN3270 Internal Trace** tab depending on the Trace Item that was selected.  
  
 From the **Internal Trace**, **Message Trace**, **API Trace** and **TN3270 Internal Trace** tabs, you can either select a single item or click **Set All**.  
  
#### To set Server trace properties  
  
1.  On the **Tools** menu, click **Trace Initiator**.  
  
2.  Click a component to trace from the list of Trace items.  
  
3.  Click **Properties**.  
  
4.  Click the appropriate trace tab.  
  
5.  Click the appropriate options for the trace, and then click **Apply**.  
  
## Trace Items - Clear All Traces  
 **Clear All Traces** will clear all trace settings and stop any running traces. If you only want to clear a specific trace item, double-click the item or select the item and click **Properties**. Then click **Clear All**.  
  
 When you select **Clear all Traces**, you will be presented with a dialog box to verify that you want to clear all trace setting.  
  
## Trace Items - Purge All Trace Files  
 **Purge All Trace Files** will delete all trace files from the Traces folder that is designated in the **Trace File Directory** tab.  
  
 When you select **Purge All Trace Files**, you will be presented with a dialog box to verify that you want to delete all trace files. If you purge all trace files, the trace settings are not deleted.