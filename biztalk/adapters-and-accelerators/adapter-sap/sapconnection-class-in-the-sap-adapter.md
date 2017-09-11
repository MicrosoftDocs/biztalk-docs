---
title: "SAPConnection class in the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SAPConnection, supported methods, classes, and constructors"
ms.assetid: a700602d-8135-4f67-a38b-770357d4e28b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SAPConnection class in the SAP adapter
The following section lists the methods and properties for the **SAPConnection** class. This represents an ADO.NET connection to the SAP application server.  
  
 This is derived from **System.Data.Common.DbConnection**.  
  
## Supported Properties  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**ConnectionString**|Get and Set|See [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).|  
|**ConnectionTimeout**|Get|Not supported. Returns 0.|  
|**Database**|Get|SAP System ID.|  
|**DataSource**|Get|This returns the name of the SAP application server host.|  
|**ServerVersion**|Get|This shows the release number for the SAP instance and not the SAP Server version. For example, if the ADO.NET client is connecting to SAP Server version 4.6 with the instance release number 620, this property will display 620.|  
|**State**|Get|Connection state. The supported states are:<br /><br /> - [System.Data.ConnectionState]<br /><br /> - Closed<br /><br /> - Open<br /><br /> - Connecting|  
  
## Supported Methods  
  
|Name|Description|  
|----------|-----------------|  
|**ChangeDatabase(string)**|Not supported.|  
|**Close()**|Closes the connection to the SAP system.|  
|**CreateCommand()**|Returns a new SAPCommand associated with this connection.|  
|**GetSchema()**|Gets the list of discovered SAP tables. All discovered tables are available in an XML file SAPDiscoveredObjects.xml. The file is located at \<installation drive>:\Program Files\Common Files\Microsoft Shared\Adapters\SAP.|  
|**GetSchema(string)**|Gets schema based on collection name. Supports the collection name “Tables”.|  
  
|Name|Description|  
|----------|-----------------|  
|**GetSchema(string, string[])**|Gets schema based on the collection name and restrictions. The table below represents the collection names and restrictions supported:|  
  
|Name|Collection Name|Restrictions|Description|  
|----------|---------------------|------------------|-----------------|  
|**GetSchema(string, string[])**|Tables|-|List of discovered SAP Tables|  
|**GetSchema(string, string[])**|Procedures|-|List of discovered RFCs|  
|**GetSchema(string, string[])**|SearchRFCs|arr[0]: Search expr|List of matching RFCs|  
|**GetSchema(string, string[])**|ImportParameters|arr[1]: RFC name|Import parameters of RFC|  
|**GetSchema(string, string[])**|ImportParameterColumn|arr[1]: RFC name<br /><br /> arr[2]: Param name|Import parameter schema|  
|**GetSchema(string, string[])**|ExportParameters|arr[1]: RFC name|Export parameters of RFC|  
|**GetSchema(string, string[])**|ExportParameterColumn|arr[1]: RFC name<br /><br /> arr[2]: Param name|Export parameter schema|  
|**GetSchema(string, string[])**|TableParameters|arr[1]: RFC name|Table parameters of RFC|  
|**GetSchema(string, string[])**|TableParameterColumn|arr[1]: RFC name<br /><br /> arr[2]: Param name|Table parameter schema|  
|**GetSchema(string, string[])**|ChangingParameters|arr[1]: RFC name|Changing parameters of RFC|  
|**GetSchema(string, string[])**|ChangingParameterColumn|arr[1]: RFC name<br /><br /> arr[2]: Param name|Changing parameter schema|  
|**GetSchema(string, string[])**|columns|arr[1]: Table name|SAP Table column schema|  
  
|Name|Description|  
|----------|-----------------|  
|**Open()**|Opens an SAP connection based on the connection string.|  
  
> [!NOTE]
>  Except for Table, Procedure, and SearchRFCs collection entries, for all other collection entries you must specify a dummy value for arr[0].  
  
## Supported Constructors  
  
|Name|Description|  
|----------|-----------------|  
|**SAPConnection()**|Creates an SAPConnection object instance.|  
|**SAPConnection(string)**|Accepts an SAP connection string. Throws an exception if the connection string is invalid.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)