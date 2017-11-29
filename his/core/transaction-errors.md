---
title: "Transaction Errors | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e557b58e-6469-4ffc-a265-75f6b26ae2ab
caps.latest.revision: 6
author: MandiOhlinger
manager: anneta
---
# Transaction Errors
The following table lists transaction error constants, values, SqlState, SqlCode, Hresult and a description of the error.  
  
||||  
|-|-|-|  
|**SqlState**|**SqlCode**|**Description**|  
|HY000|-52|**Message** : Failed to enlist on transaction, SNA LU not configured correctly.|  
|HY000|-53|**Message** : Failed to enlist on transaction, duplicate transaction detected.|  
|HY000|-54|**Message** : Failed to enlist on transaction, SNA LU busy.|  
|HY000|-55|**Message** : Failed to enlist on transaction, SNA LU 6.2 Resync Service not active.|  
|HY000|-56|**Message** : Failed to enlist on transaction, SNA LU can't connect.|  
|HY000|-57|**Message** : Failed to enlist on transaction, recovery in progress - retry.|  
|HY000|-58|**Message** : Failed to enlist on transaction; perform manual recovery or reset DTC log.|  
|HY000|-59|**Message** : Can't support transactions. MS DTC may be inactive.|  
|HY000|-60||  
|HY000|-70|**Message** : Failed to enlist on transaction: the connection is not configured for distributed units of work.|  
|HY000|-71|**Message** : Failed to enlist on transaction: the connection is already enlisted in a distributed unit of work.|  
|HY000|-72|**Message** : The connection is not running in a transaction and no explicit distributed transaction enlistment was performed. Ensure the connection is running within a valid transaction context or use explicit transaction enlistment.|  
|HY000|-73|**Message** : Failed to unenlist on transaction because no enlistment exists.|  
|HY000|-74|**Message** : Failed to enlist on transaction: the enlistment timeout has expired. The enlistment timeout is too short or prior distributed transactions have not finished processing.|  
|HY000|-75|**Message** : Distributed unit of work log error. A provider-specific error occurred.|  
|HY000|-76|**Message** : Failed to enlist on transaction: the distributed units of work over TCP/IP feature is not installed.|  
|HY000|-77|**Message** : Failed to enlist on transaction: the target host does not support distributed units of work over TCP/IP.|  
|HY000|-99||  
|HY000|-1101|**Message** : Distributed units of work are not supported on this version of Host Integration Server.<br /><br /> **Reason** : The client cannot support DB2 Distributed Unit of Work (DUW) transactions across a TCP/IP network connection, then running in 32-bit on a 64-bit operating system.<br /><br /> **Action** : Verify that the runtime execution environment when running on an x64 operating system is fully 64-bit, by changing the Visual Studio project platform target or BizTalk host application processor from x86 to x64.|  
|HY000|-2147168218|Message: A network library error has occured (-2147168218): The transaction manager has disabled its support for XA transactions.Action: Enable XA Transaction on the DB2 DRDA client computer. For more information, see http://go.microsoft.com/fwlink/p/?linkid=217339.|