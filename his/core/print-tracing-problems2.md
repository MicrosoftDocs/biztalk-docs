---
title: "Print Tracing Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25e49a59-b271-45a4-936c-cf01eed0f400
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Print Tracing Problems
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] incorporates extensive tracing within the Host Print Service components and the messages that flow between them. The [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Print Service communicates over two well-defined SNA APIs - FMI (Functional Management Interface) and the APPC (Application Program to Program Communication) API FMI is used for 3270 printing, while APPC API is used for AS/400 printing.  
  
#### For problems where the output is not correct  
  
1. If possible, isolate this print job by stopping all printing to other printer sessions. This will make it easier for support personnel to analyze when viewing traces.  
  
2. Stop the print session(s) in question.  
  
3. Enable the following traces using the SNA Manager Trace Utility:  
  
4. Select **SNAPrint**: Internal Trace Tab (Custom Events), Message Trace (all). Custom Events enables a new type of tracing called Advanced Job Logging. It traces each byte of the data stream.  
  
    Select **SNAServer**. Message Trace (Data Link Control, 3270 Messages, LU 6.2 Messages).  
  
    Reproduce the problem.  
  
    Turn the traces off **immediately** by selecting Clear All Traces button in the Tracing Items Tab.  
  
   Print another job to this Print Session, this time changing the Destination to File. This can be done in the Printing Tab for this Print Session.  
  
#### For all other problems  
  
1.  If the problem manifests itself with only one print job, isolate this job by stopping all printing to other print sessions, if possible. This will make it easier for support personnel to analyze when viewing traces.  
  
2.  Stop the print session(s) in question.  
  
3.  Enable the following traces using the SNA Manager Trace Utility:  
  
     Select **SNAPrint**: Internal Trace (all; with the exception of Custom Events), Message Trace (all).  
  
     Select **SNAServer**. Message Trace (Data Link Control, 3270 Messages, LU 6.2 Messages).  
  
     Reproduce the problem.  
  
     Turn the traces off immediately by selecting **Clear All Traces** in the **Tracing Items** tab.  
  
#### Collecting Information for support personnel  
  
1.  %snaroot%\system\config\com.cfg.  
  
2.  All traces in the %snaroot%\traces directory.  
  
3.  Application Event log.  
  
4.  Printer output file in cases where the problem is wrong output.  
  
5.  Hard copy output from the physical printer.  
  
6.  An output file and / or a hard copy output of a "successful" job. This might be another print emulator or an output from an actual IBM device.  
  
> [!NOTE]
>  Before contacting product support, obtain the following information: