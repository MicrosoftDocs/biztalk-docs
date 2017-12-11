---
title: "Host Platforms | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae1b1b43-c3bc-432b-ae21-a6bb1fc89491
caps.latest.revision: 4
---
# Host Platforms
On the mainframe platform, IBM offers a target distributed data management (DDM) server implementation in IBM Distributed File Manager (DFM), a component of IBM Data Facility Storage Management Subsystem (DFSMS). The OLE DB Provider for AS/400 and VSAM requires IBM DFSMS-DFM z/OS V1.9, V1.10 or V1.11 to support an SNA LU 6.2 network connection.  
  
 On midrange i5/OS computers, IBM has implemented a target DDM server directly in i5/OS. The OLE DB Provider for AS/400 and VSAM requires IBM i5/OS V5R4 and V6R1 or later to support either an SNA LU 6.2 network connection or TCP/IP network connection.  
  
 **Host File Types**  
  
 On the midrange i5/OS platform, the OLE DB Provider for AS/400 and VSAM supports physical and logical files with an associated external record description file. For specific limitations, see the *AS/400 DDM User's Guide*.  
  
 On the mainframe z/OS platform, the OLE DB Provider for AS/400 and VSAM supports the following data set types:  
  
 **Sequential Access Method (SAM) data sets**  
  
-   Basic Sequential Access Method data sets (BSAM)  
  
-   Queued Sequential Access Method data sets (QSAM)  
  
 **Virtual Storage Access Method (VSAM) data sets**  
  
-   Entry-Sequenced Data Sets (ESDS)  
  
-   Key-Sequenced Data Sets (KSDS)  
  
-   Fixed-Length Relative Record Data Sets (RRDS)  
  
-   Variable-Length Relative Record Data Sets (VRRDS)  
  
-   Relative Record Data Set (RRDS)  
  
-   VSAM Alternate Indexes for ESDS and KSDS data sets  
  
 **Basic Partitioned Access Method (PDS) data sets**  
  
-   Partitioned Data Set Extended members (PDSE)  
  
-   Partitioned data set (PDS) members  
  
-   Read-only support for PDSE directories  
  
-   Read-only support for PDS directories  
  
 The preceding data set types are supported by IBM DFSMS DFM.  
  
 The following data set types are not supported by DFSMS DFM and cannot be accessed using the OLE DB Provider for AS/400 and VSAM:  
  
-   VSAM Linear Data Sets (LDS)  
  
-   Generation Data Groups (GDG)  
  
-   Generation Data Sets (GDS)  
  
-   Basic Direct Access Method data sets (BDAM)  
  
-   Indexed Sequential Access Method data sets (ISAM)  
  
-   Sequential Data Striping data sets  
  
-   OpenEdition MVS Hierarchical File System (HFS) files  
  
-   Tape Media  
  
 All mainframe data sets accessible through IBM Distributed File Manager must be cataloged in an Intersystem Communications Function (ICF) catalog and reside on direct access storage devices (DASD).  
  
 **Microsoft Data Access Components**  
  
 The OLE DB Provider for AS/400 and VSAM supplied with Host Integration Server 2010 supports the following OLE DB and ADO versions:  
  
-   **OLE DB version 2.8.** The Host Integration Server 2010 data access features require the run-time libraries for OLE DB version 2.8.  
  
-   **ADO version 2.8.** The Host Integration Server data access features require the run-time libraries for ADO version 2.5.