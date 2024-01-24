---
description: "Learn more about: Error Codes for Open(PLU) Error Confirm"
title: "Error Codes for Open(PLU) Error Confirm1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error Codes for Open(PLU) Error Confirm
The following table gives the values for error code 1 that can be returned on the [Open(PLU) Error Confirm](./open-plu-error-confirm2.md) message. Error code 2 is zero, except when error code 1 is 0x0821. In this case it contains the byte offset in the **BIND** where the **BIND** failed to match the **BIND** check table.  
  
|Error code|Description|  
|----------------|-----------------|  
|0x0051|Fewer than two buffer elements were present on **Open(PLU) Response**.|  
|0x0052|System services control point (SSCP) connection is no longer active.|  
|0x0821|**BIND** checking failed: error code 2 gives byte offset in **BIND** at which the error occurred.|
