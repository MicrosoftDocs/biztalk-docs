---
title: "Data for Host Files | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b5f548-5bd9-4e0c-8edf-841a4fe98d23
caps.latest.revision: 5
ms.author: "wspubsup"
author: MandiOhlinger
manager: anneta
---
# Data for Host Files
## Platform Compatibility  
  
### Code Page Conversions  
 The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format.  
  
#### Host CCSID  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code).  
  
#### PC Code Page  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode.  
  
#### Process Binary as Character  
 The optional Process binary (CCSID 65535) as character instructs the Data Provider to convert host bytes to and from Windows character strings, based on the Host CCSID and PC Code Page. The default is false.  
  
### Data Type Mapping  
 This topic describes all data type mappings supported by the MsHostFileClient.  
  
#### ADO.NET Data Type Mapping  
 The following table defines the supported Data Provider (MsHostFileClient.HostFileType) to Host File Designer (System.Type) to IBM COBOL and RPG data types.  
  
||||||  
|-|-|-|-|-|  
|**HostFileType**|**HostFileMetaType**|**Restrictions**|**Host File Designer Type**|**COBOL**|  
|HostFileType.BigInt|System.Int64||Integer|PIC S9(n) COMP-4|  
|HostFileType.Char|System.String|Max Length: 32765; 255|String|PIC X(n)|  
|HostFileType.CharForBit|System.Byte|Max Length: 32765|Short|PIC S9(n) COMP-4|  
|HostFileType.Date|System.DateTime|Length: 10|DateTime|ISO DATE only YYYY-MM-DD|  
|HostFileType.Decimal|System.Decimal|Max Precision: 28|Decimal|PIC S9(n)V9(n) COMP-3|  
|HostFileType.Double|double||Double|COMP-2|  
|HostFileType.Graphic|System.String|Max Length: 16382; 127|String|PIC G(n)|  
|HostFileType.Int|System.Int32||Integer|PIC S9(n) COMP-4|  
|HostFileType.Numeric|System.Decimal|Max Precision: 31|Decimal|PIC S9(n)V9(n) COMP-3|  
|HostFileType.Real|float||Single|COMP-1|  
|HostFileType.SmallInt|System.Int16||Short|PIC S9(n) COMP-4|  
|HostFileType.Time|System.TimeSpan|Length: 8|DateTime|ISO TIME only HH.MM.SS|  
|HostFileType.Timestamp|System.DateTime|Length: 26|DateTime|ISO DATE and TIME YYYY-MM-DD HH.MM.SS|  
|HostFileType.UDT|System.Object|Max Length: 32739|Byte|PIC X untranslated|  
|HostFileType.VarChar|System.String|Max Length: 32739; 4045|String|PIC X(n)|  
|HostFileType.VarCharForBit|System.Byte|Max Length: 32739: 4045|Byte|PIC X untranslated|  
|HostFileType.VarGraphic|System.String|Max Length: 16369; 4045||PIC G(n)|  
  
 The following table defines the supported ADO.NET (System.Data.DbType) to Data Provider (MsHostFileClient.HostFileType) to Host File Designer (System.Type) to IBM COBOL and RPG data types.  
  
|||||||  
|-|-|-|-|-|-|  
|**DbType**|**HostFileMetaType**|**HostFileType**|**Restrictions**|**Host File Designer Type**|**COBOL**|  
|DbType.AnsiString|System.String|HostFileType.VarChar|Max Length: 32739; 4045|String|PIC X(n)|  
|DbType.AnsiStringFixedLength|System.String|HostFileType.Char|Max Length: 32765; 255|String|PIC X(n)|  
|DbType.Binary|System.Byte|HostFileType.VarCharForBit|Max Length: 32739|Byte|PIC X untranslated|  
|DbType.Boolean|System.Boolean|HostFileType.SmallInt||Boolean|PIC S9(4) COMP-4|  
|DbType.Byte|System.Byte|HostFileType.SmallInt||Short|PIC S9(n) COMP-4|  
|DbType.Currency|System.Decimal|HostFileType.Decimal|Max Precision: 31|Decimal|PIC S9(n)V9(n) COMP-3|  
|DbType.Date|System.DateTime|HostFileType.Date|Length: 10|DateTime|ISO DATE only YYYY-MM-DD|  
|DbType.DateTime|System.DateTime|HostFileType.Timestamp|Length: 26|DateTime|ISO DATE and TIME YYYY-MM-DD HH.MM.SS|  
|DbType.Decimal|System.Decimal|HostFileType.Decimal|Max Precision: 31|Decimal|PIC S9(n)V9(n) COMP-3|  
|DbType.Double|double|HostFileType.Double||Double|COMP-2|  
|DbType.Guid|System.Guid|HostFileType.VarCharForBit|Max Length: 32739|Byte|PIC X untranslated|  
|DbType.Int16|System.Int16|HostFileType.SmallInt||Short|PIC S9(n) COMP-4|  
|DbType.Int32|System.Int32|HostFileType.Int||Integer|PIC S9(n) COMP-4|  
|DbType.Int64|System.Int64|HostFileType.BigInt||Integer|PIC S9(n) COMP-4|  
|DbType.Object|System.Object|HostFileType.VarCharForBit|Max Length: 32739|Byte|PIC X untranslated|  
|DbType.SByte|SByte|HostFileType.SmallInt||Short|PIC S9(n) COMP-4|  
|DbType.Single|float|HostFileType.Real||Single|COMP-1|  
|DbType.String|System.String|HostFileType.VarChar|Max Length: 32739; 4045|String|PIC X(n)|  
|DbType.StringFixedLength|System.String|HostFileType.Char|Max Length: 32765; 255|String|PIC X(n)|  
|DbType.Time|System.TimeSpan|HostFileType.Time|Length: 8|DateTime|ISO TIME only HH.MM.SS|  
|DbType.UInt16|System.UInt16|HostFileType.SmallInt||Short|PIC 9(n) COMP-4|  
|DbType.UInt32|System.UInt32|HostFileType.Int||Integer|PIC 9(n) COMP-4|  
|DbType.UInt64|System.UInt64|HostFileType.BigInt||Integer|PIC 9(n) COMP-4|  
|DbType.VarNumeric|System.Decimal|HostFileType.Decimal||Decimal|PIC S9(n)V9(n) COMP-3|  
  
## Performance  
 This topic contains the following sections that will help you maximize performance when you are using the Data Providers for Host Files.  
  
 [Configuring for Performance](../core/data-for-host-files.md#configuringForPerformance)  
  
 [Measuring Performance](../core/data-for-host-files.md#measuringPerformance)  
  
###  <a name="configuringForPerformance"></a> Configuring for Performance  
 To improve performance, configure the providers in the following ways.  
  
#### Pool provider resources to reduce connection startup time  
 Connection Pooling is a client-side optimization that reduces connection startup time, while reducing memory utilization on the client computer. The ADO.NET provider and BizTalk Adapter support connection pooling. You can specify pooling using the ADO.NET connection string (Connection Pooling=True). Also, you can configure pooling using the Advanced dialog of the Data Source Wizard and All dialog of Data Links.  
  
 The provider maintains a cache of connections, based on a Max Pool Size property. The default pool size is 100 connections (Max Pool Size=100), which you can adjust using the All dialog of the Data Source Wizard or Data Links. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used.  
  
 Optionally, you can specify a number of seconds, to instruct the data provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the data provider will return an error to the data consumer (“connection not available”). The default is 15 seconds (Connect Timeout=15), which you can adjust using the All dialog of the Data Source Wizard or Data Links. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the data provider to wait indefinitely for an open connection in the client-side connection pool.  
  
###  <a name="measuringPerformance"></a> Measuring Performance  
 To measure performance, the data provider offers performance counters. By default performance counters are turned off. They can be turned on by changing value of the following registry key to 1:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Host Integration Server\Data Integration\UpdateCounters = 1  
  
 The data provider performance counters capture information about open connections, open statements, packets and bytes sent/received, average host (Host server) processing time, command executions, and data fetches.