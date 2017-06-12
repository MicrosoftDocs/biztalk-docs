---
title: "Basic SQL Server Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f744fe14-4134-486d-b060-9ac2d5f21c56
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic SQL Server Data Types
This topic describes how the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]surfaces basic SQL Server data types.  
  
## Supported SQL Server Data Types  
 The following table shows how the SQL Server data types are surfaced by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
|SQL Server Data Type|XSD type|.NET type|Comments|  
|--------------------------|--------------|---------------|--------------|  
|Bigint|Long|Long|-|  
|Binary|Base64Binary|Byte[]|-|  
|Bit|Boolean|Bool|-|  
|Char|String|String|-|  
|Date|DateTime|DateTime|-|  
|Datetime|DateTime|DateTime|While writing data to a Datetime field, the adapter always stores the time in GMT. If you specify the time-zone information, the adapter uses that to convert the value to a valid GMT value, and writes it to the database table. For example, 12/31/2008T23:59:59+5:30 is written to the table as 12/31/2008 6:29:59 PM.<br /><br /> However, if you do not specify the time-zone information, the adapter considers the value to be in GMT already, and writes the same value to the table. For example, 12/31/2008T23:59:59 is written to the table as 12/31/2008 11:59:59 PM.|  
|Datetime2|DateTime|DateTime|-|  
|Datetimeoffset|DateTime|DateTime|-|  
|Decimal|xsd:decimal if precision <= 28<br /><br /> xsd:string if precision > 28|Decimal if precision <= 28<br /><br /> String if precision > 28|-|  
|Filestream|Base64Binary|Byte[]|-|  
|Float|Double|Double|-|  
|Geography|String|String|-|  
|Geometry|String|String|-|  
|Hierarchyid|String|String|-|  
|Image|Base64Binary|Byte[]|-|  
|Int|Int|Int|-|  
|Money|Decimal|Decimal|-|  
|Nchar|String|String|-|  
|Ntext|String|String|-|  
|Numeric|Decimal|Decimal|-|  
|Nvarchar|String|String|-|  
|Nvarchar(Max)|String|String|-|  
|Real|Float|Float|-|  
|Smalldatetime|DateTime|DateTime|-|  
|Smallint|Short|Short|-|  
|Smallmoney|Decimal|Decimal|-|  
|SQLVariant|String|String|-|  
|Text|String|String|-|  
|Time|Duration|Timespan|-|  
|Timestamp|Base64Binary|Byte[]|-|  
|Tinyint|UnsignedByte|Byte|-|  
|Uniqueidentifier|{http://schemas.microsoft.com/2003/10/Serialization/}:guid|Guid|-|  
|Varbinary|Base64Binary|Byte[]|-|  
|Varbinary(Max)|Base64Binary|Byte[]|-|  
|Varchar|String|String|-|  
|Varchar(Max)|String|String|-|  
|XML|String|String|-|  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)