---
title: "Message Schemas for Stored Procedures, Functions, and PL-SQL APIs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d707f10-470d-4390-bb5b-0301c326f375
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Stored Procedures, Functions, and PL/SQL APIs
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces the underlying Oracle database stored procedures, functions, and PL/SQL APIs (stored procedures and functions within a package) as operations. This section describes the message structure and actions used to invoke stored procedures, functions, and PL/SQL APIs.  
  
## Message Structure of Stored Procedures, Functions, and PL/SQL APIs  
 The operations surfaced for functions and stored procedures follow a request-response message exchange pattern. The following table shows the structure of these request and response messages.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Stored Procedure Request|`<[SP_NAME] xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Supports Oracle IN and IN OUT parameters in the message body|  
|Stored Procedure Response|`<[SP_NAME]Response xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Supports Oracle OUT and IN OUT parameters in the message body|  
|Function Request|`<[FN_NAME] xmlns="[VERSION]/Functions/[SCHEMA] ">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|Supports Oracle IN and IN OUT parameters in the message body|  
|Function Response|`<[FN_NAME]Response xmlns="[VERSION]/Functions/[SCHEMA]">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|Supports Oracle OUT and IN OUT parameters in the message body<br /><br /> The function return value is returned in the \<[FN_NAME]Result> element. This is the first element in the response message. It comes before any parameters.|  
|PL/SQL API Request|`<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|Same as Function or Stored Procedure|  
|Packaged Procedure or Function Response|`<[SP_NAME]Response xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|Same as Function or Stored Procedure|  
  
 Entity descriptions:  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05.  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.  
  
 [FN_NAME] = The function to be executed; for example, FN_GETID.  
  
 [PRM1_NAME] = The name of the Oracle parameter. See the Description column for supported parameter directions for each message.  
  
 [PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.  
  
 The Oracle database supports overloading for stored procedures and functions. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports this capability by appending an overload string to the target namespace for each overloaded artifact. The value of this string is "overload1" for the first overload, "overload2" for the second overload, and so on. The following example shows the message structure for two overloaded stored procedures.  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
## Message Actions of Stored Procedures, Functions, and PL/SQL APIs  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for stored procedure, function, and PL/SQL API operations.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Message|Action|Example|  
|-------------|------------|-------------|  
|Stored Procedure Request|Procedures/[SCHEMA]/[SP_NAME]|Procedures/SCOTT/SP_INSERT|  
|Stored Procedure Response|Procedures/[SCHEMA]/[SP_NAME]/response|Procedures/SCOTT/SP_INSERT/response|  
|Function Request|Functions/[SCHEMA]/[FN_NAME]|Functions/SCOTT/FN_GETID|  
|Function Response|Functions/[SCHEMA]/[FN_NAME]/response|Functions/SCOTT/FN_GETID/response|  
|PL/SQL API Request|[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]|SCOTT/Package/CUSTOMER/SP_INSERT|  
|Packaged Stored Procedure Response|[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response|SCOTT/Package/CUSTOMER/SP_INSERT/response|  
|Packaged Function Request|[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]|SCOTT/Package/CUSTOMER/FN_GETID|  
|Packaged Function Response|[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response|SCOTT/Package/CUSTOMER/FN_GETID/response|  
|Overloaded Stored Procedure Request|[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]|SCOTT/Procedure/SP_INSERT/overload1|  
|Overloaded Stored Procedure Response|[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response|SCOTT/Procedure/SP_INSERT/overload1/response|  
  
 Entity descriptions:  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.  
  
 [FN_NAME] = The function to be executed; for example, FN_GETID.  
  
 [PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.  
  
 [OVERLOAD] = The Overload parameter. The possible values are overload1, overload2, and so on.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)