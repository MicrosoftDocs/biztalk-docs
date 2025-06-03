---
description: "Learn more about: Upgrading Existing Installation (Host Files)"
title: "Upgrading Existing Installation (Host Files)"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Upgrading Existing Installation (Host Files)
For the most recent version of Microsoft Host Integration Server documentation, see [https://msdn.microsoft.com/library/gg241192.aspx](../index.yml).  
  
## Microsoft OLE DB Provider for i Series and VSAM  
 HIS 2020 does not include or support the Microsoft OLE DB Provider for i Series and VSAM (SNAOLEDB Provider). You should use the HIS 2020 ADO.NET Framework Data Provider for Host Files (MsHostFileClient) or BizTalk Adapter for Host Files (BAHF).  
  
 HIS 2020 Data Links does not create, edit, import, or export SNAOLEDB Universal Data Link (UDL) files.  
  
 HIS 2020 Data Source Wizard does not create, edit, import, or export SNAOLEDB Universal Data Link (UDL) files. The HIS 2019 and HIS 2010 Data Source Wizard will convert SNAOLEDB UDL files into MsHostFileClient and BAHF connection string (TXT) files.  
  
 HIS 2020 Data Access Tool does not create, edit, import, or export SNAOLEDB Host Column Description (HCD) files. The HIS 2019 and HIS 2010 Host File Designer will convert SNAOLEDB HCD files into metadata assembly DLL files, which can be converted into the new HIS 2020 Host Integration Designer XML (HIDX) metadata files.  
  
## Microsoft Host File Designer Metadata Assembly Files  
 HIS 2020 ADO.NET Framework Data Provider for Host Files (MsHostFileClient) and BizTalk Adapter for Host Files (BAHF) and .NET Framework runtimes do not support Host File Designer metadata assembly DLL files. You must convert existing metadata DLLs into new Host Integration Designer XML (HIDX) metadata files using the Host Files Designer integrated within Visual Studio.  
  
 HIS 2020 Data Source Wizard includes a “Metadata definition file” edit box, in which you must provide the full path and file name of the Host Integration Designer XML (HIDX) metadata file, which the MsHostFileClient and BAHF load at runtime for encoding and decoding records in mainframe z/OS, midrange IBM i and offline host files.
