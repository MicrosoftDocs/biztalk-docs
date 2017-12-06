---
title: "Terminal Control Table1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3e7814d-54b8-4772-9c63-354883b25db6
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Terminal Control Table
The sample Terminal Control Table (TCT) defines the remote systems to CICS. Each remote system is specified using a DFHTCT definition, which includes both the name by which CICS knows the system (the SYSIDNT field), and the name by which VTAM knows the system (the NETNAME field).  
  
### Sample CICS terminal control table entries  
  
|Label|Definition|Operands|  
|-----------|----------------|--------------|  
|TP11|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6207,SYSIDNT=DC11, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP12|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6208,SYSIDNT=DC12, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP13|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU6209,SYSIDNT=DC13, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
|TP14|DFHTCT|TYPE=SYSTEM ACCMETH=VTAM, FEATURE=SINGLE,TRMTYPE=LUTYPE62, NETNAME=TPLU620A,SYSIDNT=DC14, MODENAM=LU62,CONNECT=AUTO, BUFFER=256,RUSIZE=256, TRMSTAT=(TRANSCEIVE)|  
  
## See Also  
 [CICS Tables](../core/cics-tables.md)