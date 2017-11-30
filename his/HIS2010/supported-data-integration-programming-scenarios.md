---
title: "Supported Data Integration Programming Scenarios | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf746b7a-85e3-44b5-a251-eeea2dc41500
caps.latest.revision: 11
---
# Supported Data Integration Programming Scenarios
Host Integration Server data integration technologies allow you to develop custom applications using Microsoft data access architectures and development tools. The following table lists the data sources, providers, architectures and tools available for custom application development.  
  
||||||  
|-|-|-|-|-|  
|**Data Source**|**Data Provider**|**Data Provider Namespace or Program Name**|**Data Access Architecture**|**Programming Languages**|  
|DB2|Microsoft Entity Provider for DB2|Microsoft.HostIntegration.MsDb2Client|ADO.NET Entity Framework|Microsoft Visual Basic.NET, Microsoft C#, Microsoft Visual C++|  
|DB2|Microsoft ADO.NET Data Provider for DB2|Microsoft.HostIntegration.MsDb2Client|ADO.NET|Microsoft Visual Basic.NET, Microsoft C#, Microsoft Visual C++|  
|DB2|Microsoft OLE DB Provider for DB2|DB2OLEDB|OLE DB|Microsoft Visual C++, and Microsoft Visual J++|  
|DB2|Microsoft OLE DB Provider for DB2|DB2OLEDB|Microsoft ActiveX Data Objects (ADO)|Microsoft Visual Basic, Microsoft Visual C++, and Microsoft Visual J++|  
|Host Files|Microsoft ADO.NET Data Provider for Host Files|Microsoft.HostIntegration.MsHostFileClient|ADO.NET|Microsoft Visual Basic.NET, Microsoft C#, Microsoft Visual C++|  
|Host Files|Microsoft OLE DB Provider for AS/400 and VSAM|SNAOLEDB|OLE DB|Microsoft Visual C++, and Microsoft Visual J++|  
|Host Files|Microsoft OLE DB Provider for AS/400 and VSAM|SNAOLEDB|ADO|Microsoft Visual Basic, Microsoft Visual C++, and Microsoft Visual J++|  
  
 You should use ADO.NET and the .NET Framework to develop all new custom applications to integrate important information stored in IBM DB2 databases and host file systems. You should use Component Object Model OLE DB and ActiveX Data Objects (ADO) for existing COM-based applications only. ADO.NET and the .NET Framework offer many advantages over OLE DB and ADO. These include the ability to develop XML and Web-aware applications, efficient deployment of Web Services and Windows Communication Foundation Services in addition to making it easy to develop Windows and Web form-based applications.  
  
## See Also  
 [Data Integration (Planning)](../HIS2010/data-integration-planning-2.md)