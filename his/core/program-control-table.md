---
title: "Program Control Table2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 089fb45f-7cfc-41b0-8246-4c6f94052867
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Program Control Table
The Program Control Table (PCT) defines the local transaction programs (TPs) to CICS. Each TP is specified using a DFHPCT definition that includes the name by which the TP is invoked (the TRANSID field) and the corresponding load module name from the CICS library of TPs.  
  
### Sample CICS program control table entries  
  
|TP Label|Definition|Operands|  
|--------------|----------------|--------------|  
|TRAN0|DFHPCT|TYPE=ENTRY PROGRAM=TRAN0000, TWASIZE=1000,SPURGE=NO,TPURGE=NO, RSL=00,RSLC=NO,MODENAM=NORMAL, TRANSID=TRAN0|  
|TRAN1|DFHPCT|TYPE=ENTRY PROGRAM=TRAN0001, TWASIZE=1000,SPURGE=NO,TPURGE=NO, RSL=00,RSLC=NO,MODENAM=NORMAL, TRANSID=TRAN1|  
|TRAN2|DFHPCT|TYPE=ENTRY PROGRAM=TRAN0002, TWASIZE=1000,SPURGE=NO,TPURGE=NO, RSL=00,RSLC=NO,MODENAM=NORMAL, TRANSID=TRAN2|  
|TRAN3|DFHPCT|TYPE=ENTRY PROGRAM=TRAN0003, TWASIZE=1000,SPURGE=NO,TPURGE=NO, RSL=00,RSLC=NO,MODENAM=NORMAL, TRANSID=TRAN3|  
  
 \* ****** * PROFILE TO BE USED IN LU6.2 ALLOCATE \* \*\*\*\*\*\* \*  
  
|TP Label|Definition|Operands|  
|--------------|----------------|--------------|  
||DFHPCT|TYPE=PROFILE, PROFILE=DFHCICSA, INBFMH=ALL,MODENAME=LU62|  
  
## See Also  
 [CICS Tables](../core/cics-tables.md)