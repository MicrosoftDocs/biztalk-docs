---
title: "Common Service Verbs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d2fde76-6d80-4e28-9343-5abdb9fca5cf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Common Service Verbs
This section describes each of the common service verbs (CSVs) and provides:  

- A definition of the verb.  

- The structure that defines the verb control block (VCB) used by the verb. The structure is declared in the WINCSV.H file.  

- The parameters (VCB fields) supplied to and returned by the verb. A description of each parameter is provided, along with its possible values and other information.  

- Additional information describing the use of the verb.  

  Most parameters supplied to and returned by CSVs are hexadecimal values. To simplify coding, these values are represented by meaningful symbolic constants, which are established by **#define** statements in the header file WINCSV.H. For example, the **opcode** (operation code) parameter for [CONVERT](../core/convert2.md) is the hexadecimal value represented by the symbolic constant SV_CONVERT. Use only the symbolic constants when programming CSVs.  

  This section contains:  

- [CONVERT](../core/convert2.md)  

- [COPY_TRACE_TO_FILE](../core/copy-trace-to-file1.md)  

- [DEFINE_TRACE](../core/define-trace1.md)  

- [GET_CP_CONVERT_TABLE](../core/get-cp-convert-table1.md)  

- [LOG_MESSAGE](../core/log-message2.md)  

- [TRANSFER_MS_DATA](../core/transfer-ms-data2.md)
