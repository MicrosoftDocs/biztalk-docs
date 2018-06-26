---
title: "CICS Tables1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a363f595-175a-4e1d-ad93-5b856e88ddae
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CICS Tables

## Overview
CICS uses the following tables to define LU 6.2 information:  
  
- Terminal Control Table (TCT)—defines the remote systems to CICS.  
  
- Program Control Table (PCT)—defines the local TPs to CICS.  
  
- Program Processing Table (PPT)—defines the load module characteristics to CICS.  
  
  The following sections describe these tables, and include sample definitions to illustrate how they are used.  
  
> [!NOTE]
>  These samples assume there are four TPs residing on CICS written in PL/I with the following names: TRAN0, TRAN1, TRAN2, and TRAN3.  

## Terminal Control Table
The sample Terminal Control Table (TCT) defines the remote systems to CICS. Each remote system is specified using a DFHTCT definition, which includes both the name by which CICS knows the system (the SYSIDNT field), and the name by which VTAM knows the system (the NETNAME field).  
  
### Sample CICS terminal control table entries  
  
|Label|Definition|Operands|  
|-----------|----------------|--------------|  
|TP11|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6207,SYSIDNT=DC11, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP12|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6208,SYSIDNT=DC12, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP13|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6209,SYSIDNT=DC13, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP14|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU620A,SYSIDNT=DC14, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)| 

## Program Control Table
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

## Program Processing Table
The Program Processing Table (PPT) defines the load module characteristics to CICS.  
  
 Each load module is defined using the DFHPPT definition, which includes the name of the load module (the PROGRAM field), and the language in which the module has been written. Examples are PL/I, Assembler, or COBOL (the PGMLANG field).  
  
### Sample CICS program processing table entries  
  
|Definition|Program name|Language|  
|----------------|------------------|--------------|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0000|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0001|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0002|PGMLANG=PL/I|  
|DFHPPT TYPE=ENTRY|PROGRAM=TRAN0003|PGMLANG=PL/I|  

  
## See Also  
 [CICS and VTAM Sample Definitions for LU 6.2](../core/cics-and-vtam-sample-definitions-for-lu-6-21.md)