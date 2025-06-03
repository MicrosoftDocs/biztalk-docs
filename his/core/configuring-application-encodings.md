---
description: "Learn more about: Configuring Application Encodings"
title: "Configuring Application Encodings"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Configuring Application Encodings
The DRDA Service converts base code pages and maps code points using an underlying HIS Encoder component and the Windows National Language Support (NLS) system components. The **applicationEncodings** element contains **applicationEncoding** elements for specifying default application-level encoding schemes on a per-database basis.  
  
### Default Encodings  
 The DRDA Service will encode character strings in output parameter and result set values using the encoding scheme and Coded Character Set Identifier (CCSID) specified by the DRDA Application Requester client in the ACCRDB (Access Relational Database) request.  
  
### Application Encodings  
 Optionally, the DRDA Service can encode character strings based on overrides defined in one or more applicationEncoding elements within the applicationEncodings portion of the MsDrdaService.exe.config file.  
  
#### Application Encoding Scheme  
 The **scheme** attribute instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme. This **optional** attribute accepts a **string** value. The supported values are Ebcdic, Unicode, and Ansi. The default value is **Unicode**.  
  
#### Application Encoding CCSID  
 The **ccsid** attribute instructs the DRDA Service to encode output parameter and result set values using an override CCSID (Coded Character Set Identifier), and not the DRDA AR client-requested CCSID. This **optional** attribute accepts an **integer**. The default value is **1208**.  
  
|Name|CCSID|NLS File|Euro-enabled|  
|----------|-----------|--------------|-------------------|  
|ANSI - Arabic|1256|c_1256.nls|No|  
|ANSI - Baltic|1257|c_1257.nls|No|  
|ANSI - Central Europe|1250|c_1250.nls|No|  
|ANSI - Cyrillic|1251|c_1251.nls|No|  
|ANSI - Greek|1253|c_1253.nls|No|  
|ANSI - Hebrew|1255|c_1255.nls|No|  
|ANSI - Latin I|1252|c_1252.nls|No|  
|ANSI - Turkish|1254|c_1254.nls|No|  
|EBCDIC - Arabic|420|c_20420.nls|No|  
|EBCDIC - Cyrillic (Russian)|880|c_20880.nls|No|  
|EBCDIC - Cyrillic (Serbian, Bulgarian)|1025|c_21025.nls|No|  
|EBCDIC - Denmark/ Norway|277|c_20277.nls|No|  
|EBCDIC - Denmark/ Norway (Euro)|1142|c_1142.nls|Yes|  
|EBCDIC - Finland/ Sweden|278|c_20278.nls|No|  
|EBCDIC - Finland/ Sweden (Euro)|1143|c_1143.nls|Yes|  
|EBCDIC - France|297|c_20297.nls|No|  
|EBCDIC - France (Euro)|1147|c_1147.nls|Yes|  
|EBCDIC - Germany|273|c_20273.nls|No|  
|EBCDIC - Germany (Euro)|1141|c_1141.nls|Yes|  
EBCDIC - Greek|423|c_20423.nls|No|  
|EBCDIC - Greek (Modern)|875|c_875.nls|No|  
|EBCDIC - Hebrew|424|c_20424.nls|No|  
|EBCDIC - Icelandic|871|c_20871.nls|No|  
|EBCDIC - Icelandic (Euro)|1149|c_1149.nls|Yes|  
|EBCDIC - International|500|c_500.nls|No|  
|EBCDIC - International (Euro)|1148|c_1148.nls|Yes|  
|EBCDIC - Italy|280|c_20280.nls|No|  
|EBCDIC - Italy (Euro)|1144|c_1144.nls|Yes|  
|EBCDIC - Latin America/Spain|284|c_20284.nls|No|  
|EBCDIC - Latin America/Spain (Euro)|1145|c_1145.nls|Yes|  
|EBCDIC - Multilingual/ ROECE (Latin-2)|870|c_870.nls|No|  
|EBCDIC - Thai|838|c_20838.nls|No|  
|EBCDIC - Turkish (Latin-3)|905|c_20905.nls|No|  
|EBCDIC - Turkish (Latin-5)|1026|c_1026.nls|No|  
EBCDIC - U.S./ Canada|37|c_037.nls|No|  
|EBCDIC - U.S./ Canada (Euro)|1140|c_1140.nls|Yes|  
|EBCDIC - United Kingdom|285|c_20285.nls|No|  
|EBCDIC - United Kingdom (Euro)|1146|c_1146.nls|Yes|  
  
 *Application Encoding CCSID values.*  
  
#### Application Encoding Custom CCSID  
 The customCcsid attribute instructs the DRDA Service to encode output parameter and result set values using an override custom CCSID (Coded Character Set Identifier), and not the DRDA AR client-requested CCSID. This optional attribute accepts an integer value. The default value is 1.  
  
#### Application Encoding Database  
 The **database** attribute instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme, for a specified target SQL Server database only. This **optional** attribute accepts a **string** value. The default value is an **empty string**.
