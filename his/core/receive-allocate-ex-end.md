---
title: "RECEIVE_ALLOCATE_EX_END1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f113b90c-649b-4e26-8ee7-6a0f7b5ffb04
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# RECEIVE_ALLOCATE_EX_END
The RECEIVE_ALLOCATE_EX_END verb allows an application to deregister as the attach manager for a given Local APPC LU (lu_alias). This verb must be called for each lu_alias previously passed to the RECEIVE_ALLOCATE_EX request.  
  
## Syntax  
  
```  
  
typedef struct receive_allocate_ex_end {  
       unsigned short opcode;  
       unsigned char reserv2[2];  
       unsigned short primary_rc;  
       unsigned long secondary_rc;  
       unsigned char tp_name[64];  
       unsigned char lu_alias[8];  
       unsigned char reserved3[20];  
 };  
```  
  
## Members  
 `Opcode`  
 A supplied parameter. Specifies the verb operation code, RECEIVE_ALLOCATE_EX_END.  
  
 `reserv2`  
 A reserved field.  
  
 `primary_rc`  
 If the lu_alias has not been previously registered by the application, the following error is returned:  
  
 AP_STATE_CHECK (0x0002)  
  
 `secondary_rc`  
 If the lu_alias has not been previously registered by the application, the following error is returned:  
  
 AP_ATTACH_MANAGER_INACTIVE (0x00000508)  
  
 `tp_name`  
 Must be all EBCDIC spaces (X'40')  
  
 `lu_alias`  
 Must be supplied and must match the lu_alias provided in a previous RECEIVE_ALLOCATE_EX request from the same process  
  
 `reserved3`  
 A reserved field.  
  
## Remarks  
 If the application is providing sync point support, the application needs to know when the LU-LU session limits have dropped to zero. This can be done by polling the **GET_LU_STATUS** API.  
  
 After calling **RECEIVE_ALLOCATE_EX_END** to deregister an attach manager, Host Integration Server does not tear down any existing LU6.2 sessions. To tear down an existing session, call the **DEACTIVATE_SESSION** function, supplying the appropriate lu_alias and plu_alias. If you are using Sync Level 2, deactivating the LU6.2 sessions notifies the Remote LU that the syncpoint manager has gone away and thus, a new ExchangeLogNames is required for the next connection.