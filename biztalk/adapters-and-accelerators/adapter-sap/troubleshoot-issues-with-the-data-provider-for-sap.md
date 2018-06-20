---
title: "Troubleshoot Issues with the Data Provider for SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for SAP, troubleshooting"
  - "troubleshooting, Data Provider for SAP"
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Issues with the Data Provider for SAP
This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].  
  
##  <a name="BKMK_SAPUnknownParam"></a> Unknown Parameter error using the Data Provider for SAP  
 **Problem**  
  
 The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] gives the following error:  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 **Cause**  
  
 The custom RFC, Z_EXTRACT_DATA_OO, installed in your SAP system is not the latest. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC, Z_EXTRACT_DATA_OO, to perform SELECT operations on the SAP table.  
  
 **Resolution**  
  
 You must update the custom RFC to the latest available version. This RFC, Z_EXTRACT_DATA_OO, is available with the adapterpacknoversion. For more information about how to install and uninstall the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).
  
##  <a name="BKMK_SAPOOM"></a> Out of memory exceptions when selecting data from an SAP table  
 **Problem**  
  
 The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] throws an out of memory exception when selecting data from an SAP system.  
  
 **Cause**  
  
 By default, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retrieves 10,000 rows at a time. Also, each batch of rows retrieved from the SAP system is stored in the memory. So,  
  
- If the table from which data is being retrieved contains a large number of rows, or  
  
- If the table contains columns of data types that consume a significant amount of memory,  
  
  The memory consumption by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] increases significantly and may result in an out of memory exception.  
  
  **Resolution**  
  
  You can change the maximum number of rows retrieved from the SAP system. You can do so by specifying a 'batchsize' option with the SELECT statement. For example:  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] now retrieves only 1000 rows at a time and hence does not consume large amount of memory.  
  
##  <a name="BKMK_SAPQueryExcep"></a> Exception while executing a query that takes parameters with date values  
 **Problem**  
  
 You get the following exception when you execute a query using the EXECQUERY command that has a parameter which takes a date value:  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 **Cause**  
  
 When executing queries using the EXECQUERY command, you must always specify date values in YYYYMMDD format.  
  
 **Resolution**  
  
 Make sure you specify date values in YYYYMMDD format. For example:  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <a name="BKMK_SAPNOVARIANT"></a> NO_VARIANT exception executing queries using the EXECQUERY command  
 **Problem**  
  
 You get the following exception when you execute a query using the EXECQUERY command:  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 **Cause**  
  
 There can be two probable causes for this exception:  
  
1. The query you are trying to execute has variants defined in the SAP system. Variants refer to a saved set of selection criteria that you can specify while executing an SAP query. For example, you can use variants to specify default values for queries.  
  
2. The query you are trying to execute neither has a variant defined nor it expects a parameter value to be passed.  
  
   **Resolution**  
  
3. For reason 1, make sure you specify the name of the variant associated with the query. For example:  
  
   ```  
   EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
   ```  
  
4. For reason 2, make sure you provide a dummy parameter name and value while specifying the query command. For example, if “myquery” query does not require any parameter to execute, the EXECQUERY command must be specified as:  
  
   ```  
   EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
   ```  
  
## See Also  
[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)