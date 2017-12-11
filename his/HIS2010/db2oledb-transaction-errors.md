---
title: "DB2OLEDB Transaction Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a956417-10cc-4a91-ae73-d2ef1eeb48ee
caps.latest.revision: 5
---
# DB2OLEDB Transaction Errors
The following table lists transaction error constants, values, SqlState, SqlCode, Hresult and a description of the error.  
  
|||||||  
|-|-|-|-|-|-|  
|**Const**|**Value**|**SqlState**|**SqlCode**|**Hresult**|**Description**|  
|DB2OLEDB_ENLIST_NO_XLN|XACT_E_LU_NOT_FOUND|HY000|-52|0x8004D108|**Message**: Failed to enlist on transaction, SNA LU not configured correctly.|  
|DB2OLEDB_ENLIST_DUP_TRAN|XACT_E_LU_NOT_FOUND|HY000|-53|0x8004D108|**Message**: Failed to enlist on transaction, duplicate transaction detected.|  
|DB2OLEDB_ENLIST_LU_BUSY|XACT_E_LU_BUSY|HY000|-54|0x8004D10C|**Message**: Failed to enlist on transaction, SNA LU busy.|  
|DB2OLEDB_ENLIST_NO_RESYNCSVC|XACT_E_LU_NO_RECOVERY_PROCESS|HY000|-55|0x8004D10D|**Message**: Failed to enlist on transaction, SNA LU 6.2 Resync Service not active.|  
|DB2OLEDB_ENLIST_LU_DOWN|XACT_E_LU_DOWN|HY000|-56|0x8004D10E|**Message**: Failed to enlist on transaction, SNA LU can't connect.|  
|DB2OLEDB_ENLIST_LU_RECOVERING|XACT_E_LU_RECOVERING|HY000|-57|0x8004D10F|**Message**: Failed to enlist on transaction, recovery in progress - retry.|  
|DB2OLEDB_ENLIST_XLN_MISMATCH|XACT_E_LU_RECOVERY_MISMATCH|HY000|-58|0x8004D110|**Message**: Failed to enlist on transaction; perform manual recovery or reset DTC log.|  
|DB2OLEDB_DTC_INIT_FAIL|REGDB_E_CLASSNOTREG|HY000|-59|0x80040154|**Message**: Can't support transactions. MS DTC may be inactive.|  
|DB2OLEDB_DUW_UNPROTECTED||HY000|-60|||  
|DB2OLEDB_DUWTCP_NOT_CONFIGURED|IDS_NOT_DUW_CONFIGURED|HY000|-70||**Message**: Failed to enlist on transaction: the connection is not configured for distributed units of work.|  
|DB2OLEDB_DUWTCP_ALREADY_ENLISTED|IDS_ALREADY_ENLISTED|HY000|-71||**Message**: Failed to enlist on transaction: the connection is already enlisted in a distributed unit of work.|  
|DB2OLEDB_DUWTCP_NO_TRANSACTION|IDS_NO_TRANSACTION|HY000|-72||**Message**: The connection is not running in a transaction and no explicit distributed transaction enlistment was performed. Ensure the connection is running within a valid transaction context or use explicit transaction enlistment.|  
|DB2OLEDB_DUWTCP_CANNOT_UNENLIST|IDS_CANNOT_UNENLIST|HY000|-73||**Message**: Failed to unenlist on transaction because no enlistment exists.|  
|DB2OLEDB_DUWTCP_ENLISTMENT_TIMEOUT|IDS_ENLISTMENT_TIMEOUT|HY000|-74||**Message**: Failed to enlist on transaction: the enlistment timeout has expired. The enlistment timeout is too short or prior distributed transactions have not finished processing.|  
|DB2OLEDB_DUWTCP_LOG_FAILURE|IDS_DUW_LOG_FAILURE|HY000|-75|0x80004005|**Message**: Distributed unit of work log error. A provider-specific error occurred.|  
|DB2OLEDB_DUWTCP_NOT_INSTALLED|IDS_DUW_NOT_INSTALLED|HY000|-76||**Message**: Failed to enlist on transaction: the distributed units of work over TCP/IP feature is not installed.|  
|DB2OLEDB_DUWTCP_NO_HOST_SUPPORT|IDS_DUW_HOST_NOT_SUPPORTED|HY000|-77||**Message**: Failed to enlist on transaction: the target host does not support distributed units of work over TCP/IP.|  
|DB2OLEDB_SQL_ERROR||HY000|-99|||  
|DB2OLEDB_DUW_NOT_SUPPORTED||HY000|-1101||**Message**: Distributed units of work are not supported on this version of Host Integration Server.<br /><br /> **Reason**: The client cannot support DB2 Distributed Unit of Work (DUW) transactions across a TCP/IP network connection, then running in 32-bit on a 64-bit operating system.<br /><br /> **Action**: Verify that the runtime execution environment when running on an x64 operating system is fully 64-bit, by changing the Visual Studio project platform target or BizTalk host application processor from x86 to x64.|