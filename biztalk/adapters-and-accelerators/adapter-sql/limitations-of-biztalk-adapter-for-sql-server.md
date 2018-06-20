---
title: "Limitations of BizTalk Adapter for SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Limitations of BizTalk Adapter for SQL Server
The following are known limitations for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:  
  
- The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support synonyms created in the SQL Server database. For information about synonyms in SQL Server, see [http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111).  
  
- If you change the system time of the computer running the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host, the time is not updated automatically in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host. This could lead to incorrect behavior of the inbound operations that use the receive port of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. As a workaround, you must restart the host instance that has a receive port after you have changed the system time of the computer running it.  
  
- If a parameter name in a stored procedure contains 127 or more characters, you cannot execute the stored procedure using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. This is due to the limitation of ADO.NET.  
  
- The WSDL the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] generates, when converted to a proxy, exposes the DateTimeOffset column as System.DateTime. This data type cannot store time zone information. As a consequence, any date/time value the adapter sends to the proxy will be converted into local time in the .NET application. If you wish to keep the time zone information, you must change the interface of your proxy to use the String type instead of System.DateTime. Then, use XmlConvert.ToDateTimeOffset to create a Sytstem.DateTimeOffset object, which can store the timezone information.  
  
## See Also  
 [UNderstand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)