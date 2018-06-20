---
title: "Trace Viewer1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd2b95d3-9e83-4b8c-ba3a-a99923fbac1a
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Trace Viewer
Microsoft Host Integration Server Trace Viewer is graphical user interface to create, view and analyze trace results when trying to diagnose a problem.  
  
## Run Trace Viewer  
 To run Trace Viewer, on the **Start** menu, point to **All Programs**, **Microsoft Host Integration Server 2013**, and then click **Trace Viewer**.  
  
## Open a Trace File  
 To open a trace file:  
  
1. On the **File** menu, click **Open**, and then click **Trace File**.  
  
2. In the **Open File** dialog box, select the trace data file you want to open.  
  
   To open a recent trace file:  
  
3. On the **File** menu, click **Recent Files**, and then click a recent trace data file.  
  
## Save Trace Results to a File  
 To save trace results to a text file:  
  
1. On the **File** menu, click **Save As**, and then click **Text**.  
  
2. In the **Save As** dialog, specify a path and filename, and then click Save.  
  
   To save trace results to a comma separated file:  
  
3. On the **File** menu, click **Save As**, and then click **Comma Separated**.  
  
4. In the **Save As** dialog, specify a path and filename, and then click **Save**.  
  
## File Menu Keyboard Shortcuts  
  
|**Menu Action**|**Shortcut**|  
|---------------------|------------------|  
|Display open file dialog box|ALT+F,O|  
|Close trace file|CTRL+F4|  
|Display save file as text dialog box|ALT+F,S,T|  
|Display save file as CSV dialog box|ALT+F,S,T|  
|Exit Trace Viewer|ALT+F4|  
  
## Copy a Trace File Line  
 To copy a trace data line:  
  
1.  On the **Edit** menu, click any row in the trace results, and then click **Copy**.  
  
## Find a Trace Data Value  
 To find a trace data value:  
  
1.  Click any row in the trace results.  
  
2.  On the **Edit** menu, and then click **Find**.  
  
3.  In the **Find** dialog box, enter a search value in the **Find what** text box.  
  
    |**Option**|**Description**|  
    |----------------|---------------------|  
    |Find what|Enter the text that you want to search for. The search matches any string containing the specified string.|  
    |Look in|Click a data column to search in the trace.|  
    |Direction|Select the direction to search up or down in the trace.|  
    |Match case|Specify to match the case of the find string.|  
    |Include Details|Choose to include trace details.|  
  
4.  To find the next occurrence of a value, click **Find**.  
  
5.  To close the Find dialog, click **Cancel**.  
  
## Edit Menu Keyboard Shortcuts  
  
|**Menu Action**|**Shortcut**|  
|---------------------|------------------|  
|Copy trace data line|CTRL+C|  
|Find trace data value|CTRL+F|  
|Find next trace data value|F3|  
|Find previous trace data value|SHIFT+F3|  
|Go to line number|CTRL+G|  
|Set or remove bookmark|CTRL+F2|  
|Next bookmark|F2|  
|Previous bookmark|SHIFT+F2|  
|Clear bookmarks|CTRL+SHIFT+F2|  
  
## View Toolbar and Status  
 To view toolbar and status:  
  
1.  Click **Tools**, and then click **Toolbar**.  
  
2.  Click **Tools**, and then click **Status**.  
  
## View Menu Keyboard Shortcuts  
  
|**Menu Action**|**Shortcut**|  
|---------------------|------------------|  
|Display Toolbar toggle on and off|ALT+V,T|  
|Display Status toggle on and off|ALT+V,S|  
  
## Filter a Trace Data Value  
 To filter a trace data value:  
  
1.  Click any row in the trace results.  
  
2.  On the **Tools** menu, and then click **Filter**.  
  
3.  In the **Filter** dialog box, click one or more **Thread** values, and then click **OK**.  
  
## Trace Viewer Options  
 To set Trace Viewer tracing font options:  
  
1. Click **Tools** menu, click **Options**, and then click **Tracing Font**.  
  
2. In the **Font** dialog, optionally select choice of **Font**, **Font style**, **Size**, **Effects**, **Script**, and then click **OK**.  
  
   To set Trace Viewer editor font options:  
  
3. Click **Tools** menu, click **Options**, and then click **Editor Font**.  
  
4. In the **Font** dialog, optionally select choice of **Font**, **Font style**, **Size**, **Effects**, **Script**, and then click **OK**.  
  
   To set Trace Viewer display columns options:  
  
5. Click **Tools** menu, click **Options**, and then click **Display Columns**.  
  
6. In the **Display Columns** dialog, optionally select from **Available Columns**, and then click **OK**.  
  
## Trace File Options  
 To split a large trace file:  
  
1.  Click **Tools** menu, click **Split a Large Trace file**.  
  
2.  Click **Browse**, and then specify a **Filename** in the **File Open** dialog.  
  
3.  Specify the **Size of Pieces**, and then click **OK**.  
  
## Tools Menu Keyboard Shortcuts  
  
|**Menu Action**|**Shortcut**|  
|---------------------|------------------|  
|Display filter dialog|ALT+T,F|  
|Display tracing font options dialog|ALT+T,O,T|  
|Display editor font options dialog|ALT+T,O,E|  
|Display column options|ALT+T,O,C|  
|Display split a large trace file dialog|ALT+T,O,L|