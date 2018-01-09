---
title: "Windows CSV Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eabeec74-ad30-4991-828e-57243df45743
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Windows CSV Overview
Common service verbs (CSVs) are a set of programming functions provided by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. The CSVs provide convert, log, trace, and transfer services to applications.  
  
 The CSVs and information presented in this section represent an evolving CSV API that is composed of IBM Extended Services for OS/2 and a set of Microsoft Windows extensions that allow for registering and deregistering the application, and that provide an asynchronous entry point for [TRANSFER_MS_DATA](./transfer-ms-data2.md).  
  
 This section describes the verbs available to you and explains how to use them with your applications. A detailed description of each verb is provided in the reference portion of the SDK.  
  
 The CSVs are as follows:  
  
 [CONVERT](./convert2.md)  
 Converts a character string from ASCII to EBCDIC or from EBCDIC to ASCII.  
  
 [COPY_TRACE_TO_FILE](./copy-trace-to-file1.md)  
 Concatenates the contents of the individual application programming interface (API)/link service trace files to form a single trace file.  
  
 [DEFINE_TRACE](./define-trace1.md)  
 Enables or disables tracing for specific APIs.  
  
 [GET_CP_CONVERT_TABLE](./get-cp-convert-table1.md)  
 Creates and returns a 256-byte conversion table to translate character strings from a source code page to a target code page.  
  
 [LOG_MESSAGE](./log-message2.md)  
 For OS/2 only, takes a message from a message file, adds specified data to it, and records the message in the error log file. This verb optionally displays the message on the user's screen.  
  
 [TRANSFER_MS_DATA](./transfer-ms-data2.md)  
 Builds a Systems Network Architecture (SNA) request unit (RU) containing Network Management Vector Transport (NMVT) data. The verb can send the NMVT data to NetView for centralized problem diagnosis and resolution. The data is optionally logged in the event log for Windows.  
  
 This section contains:  
  
-   [Host Integration Server Asynchronous Support](../core/host-integration-server-asynchronous-support]2.md)  
  
-   [Before Using Windows CSV](../core/windows-csv-considerations]2.md)  
  
-   [Using CSVs in C Programs](../core/csvs-in-c-programs]1.md)  
  
-   [Sample Programs](../core/sample-programs1.md)  
  
-   [CSV Verb Control Block](../core/csv-verb-control-block2.md)  
  
-   [Bit Ordering](../core/bit-ordering2.md)  
  
-   [WINCSV Definition](../core/wincsv-definition1.md)  
  
-   [WINCSV.H File](../core/wincsv-h-file2.md)  
  
-   [Issuing a CSV](../core/issuing-a-csv1.md)