---
title: "DDM Record-Level Access | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe5370a6-8aa6-449c-8bf7-62913484abdf
caps.latest.revision: 4
---
# DDM Record-Level Access
The OLE DB Provider for AS/400 and VSAM provides record-oriented access to host files. There is no need to perform bandwidth-intensive bulk file transfers of entire host files to access data on the host. Providing users with direct record-level access reduces the development time to build and deploy new data integration solutions. Accessing only the target records, as opposed to entire host files, helps ensure data integrity.  
  
 The OLE DB interface provided by the OLE DB Provider for AS/400 and VSAM supports the following features depending on the host platform and host file type:  
  
-   Set attributes and a record description of a host file (column information).  
  
-   Lock files and records.  
  
-   Position to the first record or the last record in a file.  
  
-   Navigate to the previous or next record in a file.  
  
-   Seek to a record, based on an index.  
  
-   Change records in a file.  
  
-   Insert new records and delete records in a file.  
  
-   Preserve file and record attributes.  
  
 The OLE DB Provider for AS/400 and VSAM is a source distributed data management (DDM) requester implementation that can initiate DDM commands to be serviced by a remote host-based target DDM server. On the Windows operating system, the Microsoft DDM requester can run as a Windows service for use by multiple concurrent OLE DB consumers. This enables the DDM service to integrate with other host applications using the IBM DDM protocol and DDM servers that are resident on the host. Microsoft host based software is not required. For more information, see [Platforms Supported by the OLE DB Provider for AS/400 and VSAM](../HIS2010/host-platforms.md). IBM offers DDM servers for the most popular host environments.