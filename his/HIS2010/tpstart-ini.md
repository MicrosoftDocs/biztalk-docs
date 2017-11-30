---
title: "TPSTART.ini | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a42bc66-db56-4007-b915-d586054465b5
caps.latest.revision: 4
---
# TPSTART.ini
You can use TpStart.ini to specify custom tracing options when using TPSTART.exe.  
  
 The TpStart.ini file should be placed in the \<snaroot> folder.  
  
 **TpStart.ini sample**  
  
```  
  
[TpStart]  
HIDE=0  
QSIZE=64  
TRACE=1  
FILE=C:\traces\tpstart.txt  
LEVEL=0  
FSIZE=2000000  
  
Details for the entries are:  
  
HIDE - 1: Hides the icon  
            0: Shows the icon  
  
QSIZE - Size of the pending queue, MIN=16,MAX=256  
             Note, if QSIZE is not included in the ini file, a size of 16 is used  
  
TRACE - 1: Enable tracing  
               0: Disable tracing  
  
FILE - The path and filename to be created for the trace, note the folder must already exist  
  
LEVEL - The level of tracing (0 - 10):  0 - the most detailed tracing,  10 - no tracing  
  
FSIZE - Maximum file size, MIN=10000, MAX=0xFFFFFFFF  
             Note, if FSIZE is not included in the ini file, a size of 10000 is used.  
```  
  
 For additional information about TpStart.exe, see KB article 137074 at [http://support.microsoft.com/kb/137074](http://support.microsoft.com/kb/137074).  
  
## See Also  
 [TPSTART](../HIS2010/tpstart.md)