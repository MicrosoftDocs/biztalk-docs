---
title: "Common Service Verbs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03623022-3afe-4902-ac64-a5cdcb67ba65
caps.latest.revision: 3
---
# Common Service Verbs
This section describes each of the common service verbs (CSVs) and provides:  
  
-   A definition of the verb.  
  
-   The structure that defines the verb control block (VCB) used by the verb. The structure is declared in the WINCSV.H file.  
  
-   The parameters (VCB fields) supplied to and returned by the verb. A description of each parameter is provided, along with its possible values and other information.  
  
-   Additional information describing the use of the verb.  
  
 Most parameters supplied to and returned by CSVs are hexadecimal values. To simplify coding, these values are represented by meaningful symbolic constants, which are established by **#define** statements in the header file WINCSV.H. For example, the **opcode** (operation code) parameter for [CONVERT](../HIS2010/convert1.md) is the hexadecimal value represented by the symbolic constant SV_CONVERT. Use only the symbolic constants when programming CSVs.  
  
 This section contains:  
  
-   [CONVERT](../HIS2010/convert1.md)  
  
-   [COPY_TRACE_TO_FILE](../HIS2010/copy-trace-to-file2.md)  
  
-   [DEFINE_TRACE](../HIS2010/define-trace2.md)  
  
-   [GET_CP_CONVERT_TABLE](../HIS2010/get-cp-convert-table2.md)  
  
-   [LOG_MESSAGE](../HIS2010/log-message1.md)  
  
-   [TRANSFER_MS_DATA](../HIS2010/transfer-ms-data1.md)