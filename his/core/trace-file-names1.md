---
title: "Trace File Names1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c7bda50-aa14-461c-814b-43529140de38
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Trace File Names
Each trace file has two names associated with it, \<*Filename*1>.atf and \<*Filename*2>.atf.  
  
 Traces are written to the first file until it reaches the specified size, then to the second until it reaches that size, and so on alternating between the two files.  
  
 By default, the trace files are stored in the \Program Files\Host Integration Server\Traces folder, with an .atf file name extension.  
  
 The following table lists the file names used by Trace:  
  
|Service|Type of tracing|File names used|File names used|  
|-------------|---------------------|---------------------|---------------------|  
|**SnaBase**|Internal|Napint1.atf|Napint2.atf|  
||Message|Napmsg1.atf|Napmsg2.atf|  
|**SnaServer (PU 2.1 node)**|Internal|Nodeint1.atf|Nodeint2.atf|  
||Message|Nodemsg1.atf|Nodemsg2.atf|  
|**Link service**|Internal|Linkint1.atf|Linkint2.atf|  
||Message|Linkmsg1.atf|Linkmsg2.atf|  
|**NetView Alert**|Internal|Nvaint1.atf|Nvaint2.atf|  
||Message|Nvamsg1.atf|Nvamsg2.atf|  
||API|Nvaapi1.atf|Nvaapi2.atf|  
|**NetView command**|Internal|Nvcint1.atf|Nvcint2.atf|  
||Message|Nvcmsg1.atf|Nvcmsg2.atf|  
||API|Nvcapi1.atf|Nvcapi2.atf|  
|**SNA applications**|Internal|Cliint1.atf|Cliint2.atf|  
||Message|Cliimsg1.atf|Cliimsg2.atf|  
||API|Cliiapi1.atf|Cliapi2.atf|  
|**Manage Agent**|Internal|Mgaint1.atf|Mgaint2.atf|  
||Message|Mgamsg1.atf|Mgamsg2.atf|  
|**Manage Client**|Internal|Mgcint1.atf|Mgcint2.atf|  
||Message|Mgcmsg1.atf|Mgcmsg2.atf|  
|**SNA Manager**|Internal|Expint1.atf|Expint2.atf|  
||Message|Expmsg1.atf|Expmsg2.atf|  
||API|Expapi1.atf|Expapi2.atf|  
|**TN3270**|Internal|tn3int1.atf|tn3int2.atf|  
||Message|tn3msg1.atf|tn3msg2.atf|  
||API|tn3api1.atf|tn3api2.atf|  
|**TN5250**|Internal|tn5int1.atf|tn5int2.atf|  
||Message|tn5msg1.atf|tn5msg2.atf|  
||API|tn5api1.atf|tn5api2.atf|  
|**Host Print Service**|Internal|sprtint1.aft|sprtint2.aft|  
||Message|sprtmsg1.atf|sprtmsg2.atf|  
||API|sprtapi1.atf|sprtapi2.atf|  
|**NetView**|Internal|mnvtint1.atf|mnvtint2.atf|  
|**DDM**|Internal|ddmint1.atf|ddmint2.atf|  
||Message|ddmmsg1.atf|ddmmsg2.atf|  
||API|ddmapi1.atf|ddmapi2.atf|  
|**DB2 Network Library**|Internal|db2int1.atf|db2int2.atf|  
||Message|db2msg1.atf|db2msg2.atf|  
||API|db2api1.atf|db2api2.atf|  
  
## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)