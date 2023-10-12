---
description: "Learn more about: How to Capture a Memory Dump of a BizTalk Process"
title: "How to Capture a Memory Dump of a BizTalk Process"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Capture a Memory Dump of a BizTalk Process
Under certain circumstances it may be necessary to capture a memory dump of a process running on a BizTalk Server to perform an in depth analysis of the process. Situations that may require analysis of a memory dump include the following:

- When a process is unresponsive.

- When a process is crashing.

- When a process leaks memory.

  This section includes the steps that should be followed to capture the appropriate type of memory dump.

## Installation of the IIS Diagnostics Toolkit
For each topic in this section, to capture a memory dump, you have to use the **Debug Diagnostics Tool** in the IIS Diagnostics Toolkit. To install this tool, follow these steps:

1. Download the Internet Information Services (IIS) Diagnostics Toolkit (**iisdiag.msi**).

2. Double-select the **iisdiag.msi** package to start the IIS Diagnostics Toolkit setup program. Choose the **Custom** setup type.

3.  In the **Custom Setup** dialog, ensure that the option for the **Debug Diagnostics Tool 1.0** is enabled and complete the steps in the setup program.

## In This Section

-   [How to Capture a Memory Dump of a Process that is Non Responsive](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)

-   [How to Capture a Memory Dump of a Process that is Crashing](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)

-   [How to Capture a Memory Dump of a Process that is Leaking Memory](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)

-   [How to Use Debug Diagnostics to Analyze a Memory Dump](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)
