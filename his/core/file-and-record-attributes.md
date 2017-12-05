---
title: "File and Record Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6a70534-958d-4382-9fe2-e012c0a71cc0
caps.latest.revision: 6
---
# File and Record Attributes
By definition, the record description is not part of the record I/O architecture in distributed data management (DDM). Traditionally, applications must embed the record format as part of the application program. This creates a burden on the application and is inconsistent with the personal computer-based data access standards, such as OLE DB.  
  
 To solve this problem, the OLE DB Provider for AS/400 and VSAM uses an external host column description (HCD) file stored on the computer that enables administrators to describe the host record format. At run time, the OLE DB Provider for AS/400 and VSAM transparently converts the host data to computer data using the local HCD information. Before a user program can view or open a host file using the OLE DB Provider for AS/400 and VSAM, the user program must create a valid record description file or entry for the target host file.  
  
 The OLE DB Provider for AS/400 and VSAM includes a Visual Studio designer to allow developers to easily create these local record description files and the necessary registry settings for data sources. The Host File Designer makes it relatively easy to create HCD files without knowing the HCD file format. The [Host Column Description](../core/host-column-description.md) file format is documented in the Data Integration Programmer's Reference.  
  
 At runtime, the data conversion process occurs in two steps. First, the host data is converted from host packed data by the DDM client. The HCD file is used during this step to convert host data types to C data types, which are based on the SQL data types defined in the ANSI/ISO SQL-92 standard. Second, the SNAOLEDB provider converts SQL C data types to OLE DB data types.  
  
 The use of an HCD file is not necessary to describe the record format for data stored in the midrange i5/OS computer because the OLE DB Provider for AS/400 and VSAM automatically detects that the target host system is an AS/400 and uses the appropriate DDM commands to retrieve the record description. If the system administrator or the OLE DB application developer wants to use an HCD file instead of retrieving the AS/400 record description, this behavior can be forced by setting the configuration of the **Host Column Description File** property using OLEDB Data Links or the Data Access Wizard in the Data Access Tool.