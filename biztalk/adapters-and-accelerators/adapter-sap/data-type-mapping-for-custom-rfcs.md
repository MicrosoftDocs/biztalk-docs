---
description: "Learn more about: Data Type Mapping for Custom RFCs"
title: "Data Type Mapping for Custom RFCs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Type Mapping for Custom RFCs
The following table provides information about SAP data types and how they are mapped to .NET data types for the Z_EXTRACT_DATA_OO RFC. This custom RFC is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
> [!NOTE]
>  For the Z_EXECUTE_SAP_QUERY, which is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to execute the EXECQUERY command, all SAP data types are converted to .NET string types.  
  
|SAP Data Type|.NET Data Type|  
|-------------------|--------------------|  
|ACCP|-   Int32<br />-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.|  
|CHAR|String|  
|CLNT|String|  
|CUKY|String|  
|CURR|Decimal, if precision less than or equal to 28<br /><br /> String, if precision greater than 28|  
|DATS|-   DateTime<br />-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.|  
|DEC|Decimal|  
|FLTP|Double|  
|INT1|Byte|  
|INT2|Int16|  
|INT4|Int32|  
|LANG|String|  
|NUMC|-   Int32, if field length less than or equal to 9<br />-   Int64, if field length greater than 9 and less than or equal to 19<br />-   String, if greater than 19<br />-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.|  
|PREC|Int16|  
|QUAN|Decimal|  
|RAW|Byte []|  
|RSTR|Byte []|  
|SSTR|String|  
|STRG|String|  
|TIMS|-   TimeSpan<br />-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.|  
|UNIT|String|  
|LCHR|String|  
|LRAW|Byte []|  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)
