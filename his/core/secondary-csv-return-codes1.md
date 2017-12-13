---
title: "Secondary CSV Return Codes1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c21f4991-53f6-4c7e-b1d4-2f5409a7ef65
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Secondary CSV Return Codes
## 00000006  
 SV_INVALID_DATA_SEGMENT  
 The data buffer containing the source or target string did not fit in one segment, or the target segment was not a read/write segment. This applies only to the Microsoft® Windows® and OS/2 systems.  
  
## 00000301  
 SV_SSCP_PU_SESSION_NOT_ACTIVE  
 The Network Management Vector Transport (NMVT) was not sent; either the system services control point-physical unit (SSCP-PU) session was not active, the node configured to receive diagnostic information was not active, or no network management connection was configured.  
  
## 00000302  
 SV_DATA_EXCEEDS_RU_SIZE  
 The data to be sent was too long. The length of the user-supplied data plus headers and added subvectors must fit in a single request unit (RU) that is not more than 512 bytes long.  
  
## 00000303  
 SV_INVALID_DATA_TYPE  
 The **data_type** parameter contained an invalid value.  
  
## 00000401  
 SV_INVALID_DIRECTION  
 The **direction** parameter contained an invalid value.  
  
## 00000402  
 SV_INVALID_CHARACTER_SET  
 The **char_set** parameter contained an invalid value.  
  
## 00000404  
 SV_INVALID_FIRST_CHARACTER  
 The first character of a type A source string was invalid.  
  
## 00000405  
 SV_TABLE_ERROR  
 One of the following occurred:  
  
-   The file containing the user-written type G conversion table was not specified by the environment variable CSVTBLG.  
  
-   The table was not in the correct format.  
  
-   The file specified by the CSVTBLG variable was not found.  
  
## 00000406  
 SV_CONVERSION_ERROR  
 One or more characters in the source string were not found in the conversion table. These characters were converted to nulls (0x00). The verb still executed.  
  
## 00000621  
 SV_INVALID_MESSAGE_ACTION  
 The **msg_act** parameter contained an invalid value.  
  
## 00000624  
 SV_INVALID_SET  
 The **dt_set** parameter contained an invalid value.  
  
## 00000629  
 SV_COPY_TRACE_IN_PROGRESS  
 A previously issued [COPY_TRACE_TO_FILE](../core/copy-trace-to-file1.md) is still in progress.  
  
## 0000062A  
 SV_TRACE_NOT_STOPPED  
 A trace was in progress when the verb was issued.  
  
## 0000062B  
 SV_INVALID_FILE_OPTION  
 A value other than SV_NEW or SV_OVERWRITE was specified for **file_option**.  
  
## 0000062C  
 SV_TRACE_BUFFER_EMPTY  
 The trace storage buffer did not contain any data.  
  
## 0000062F  
 SV_INVALID_RESET_TRACE  
 The **reset_trc** parameter contained an invalid value.  
  
## 00000630  
 SV_INVALID_CHAR_NOT_FOUND  
 The **char_not_fnd** parameter contained an invalid value.  
  
## 00000631  
 SV_INVALID_SOURCE_CODE_PAGE  
 The code page specified by **source_cp** is not supported.  
  
## 00000632  
 SV_INVALID_TARGET_CODE_PAGE  
 The code page specified by **target_cp** is not supported.  
  
## 030000AB  
 SV_SERVER_COMM_FAILURE  
 The connection to the server was lost due to physical path problems; for example, the server may have been powered off.