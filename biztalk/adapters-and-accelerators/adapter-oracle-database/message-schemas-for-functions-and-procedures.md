---
title: "Message Schemas for Functions and Procedures | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functions and procedures, message structure of"
  - "functions and procedures, message actions of"
ms.assetid: 90b77b15-a4c6-487d-a09e-a078ceddfd1e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Functions and Procedures
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces Oracle database functions and stored procedures as operations. This section describes the message structure and actions used to invoke functions and procedures.  

## Message Structure of Functions and Procedures  
 The operations surfaced for functions and stored procedures follow a request-response message exchange pattern. The following table shows the structure of these request and response messages.  

|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Stored Procedure Request|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Supports Oracle IN and IN OUT parameters in the message body|  
|Stored Procedure Response|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Supports Oracle OUT and IN OUT parameters in the message body|  
|Function Request|`<[FN_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|Supports Oracle IN and IN OUT parameters in the message body|  
|Function Response|`<[FN_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|Supports Oracle OUT and IN OUT parameters in the message body<br /><br /> - The function return value is returned in the \<[FN_NAME]Result\> element. This is the first element in the response message. It comes before any parameters.|  
|Packaged Procedure or Function Request|`<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Same as Function or Stored Procedure|  
|Packaged Procedure or Function Response|`<[SP_NAME]Response xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Same as Function or Stored Procedure|  

 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

 [SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.  

 [FN_NAME] = The function to be executed; for example, FN_GETID.  

 [PRM1_NAME] = The name of the Oracle parameter. See the Description column for supported parameter directions for each message.  

 [PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.  

 The Oracle database supports overloading for stored procedures and functions. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports this capability by appending an overload string to the target namespace for each overloaded artifact. The value of this string is "overload1" for the first overload, "overload2" for the second overload, and so on. The following example shows the message structure for two overloaded stored procedures.  

```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  

Stored Procedure Overload 2:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  

## Message Actions of Functions and Procedures  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the following message actions for stored procedure and function operations.  


|               Message                |                                              Action                                              |                                          Example                                           |
|--------------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|       Stored Procedure Request       |            http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]            |          http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT           |
|      Stored Procedure Response       |       http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/response        |      http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/response      |
|           Function Request           |            http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]             |           http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID            |
|          Function Response           |        http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Function/[FN_NAME]/response        |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETID/response       |
|  Packaged Stored Procedure Request   |     http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]      |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT       |
|  Packaged Stored Procedure Response  | http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response |  http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/SP_INSERT/response   |
|      Packaged Function Request       |     http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]      |       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID        |
|      Packaged Function Response      | http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response |   http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/CUSTOMER/FN_GETID/response   |
| Overloaded Stored Procedure Request  |      http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]       |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1      |
| Overloaded Stored Procedure Response |  http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response  | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_INSERT/overload1/response |

 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

 [SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.  

 [FN_NAME] = The function to be executed; for example, FN_GETID.  

 [PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.  

 [OVERLOAD] = The Overload parameter. The possible values are overload1, overload2, and so on.  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)