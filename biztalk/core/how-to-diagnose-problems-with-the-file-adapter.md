---
description: "Learn more about: How to Diagnose Problems with the File Adapter"
title: "How to Diagnose Problems with the File Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f06089a5-4747-4879-a796-157088868dba
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Diagnose Problems with the File Adapter
This section contains steps that can be followed to help diagnose problems with the File adapter.

### Run the FileMon Utility to diagnose errors that occur using the File Receive or File Send Adapter

1.  Download the FileMon utility from [www.sysinternals.com](https://go.microsoft.com/fwlink/?LinkId=66235).

2.  Install the Filemon utility on the server that hosts the folder or share that is being read from or written to by the File Adapter.

3.  Launch the Filemon utility and apply a filter to monitor only file accesses that are being made by the BizTalk Host instance that the file adapter handlers are running in (for example BTSNTSvc.exe).

4.  Run the scenario that caused the problem.

5.  Disable file monitoring in the Filemon utility, then save the generated log file to disk.

6.  Review the generated log file for any errors.

    > [!NOTE]
    >  FileMon is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this program. Use of this program is entirely at your own risk.

## See Also
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)
 [Troubleshooting the File Adapter](../core/troubleshooting-the-file-adapter.md)
