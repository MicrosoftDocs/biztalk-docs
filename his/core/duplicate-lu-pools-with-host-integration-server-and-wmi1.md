---
description: "Learn more about: Duplicate LU Pools with Host Integration Server and WMI"
title: "Duplicate LU Pools with Host Integration Server and WMI1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Duplicate LU Pools with Host Integration Server and WMI
A VBScript ImportExport sample program written in Microsoft Visual Basic Scripting Edition (VBScript) is provided as part of the Host Integration Server SDK. This tool enables configuration information from Host Integration Server to be exported and saved to a text file using Windows Management Instrumentation (WMI) in MOF format. This text file can also be changed and imported using this sample program to change configuration information.  
  
 A potential problem using WMI can occur with duplicate LU pools that can be illustrated using this sample program. Typically, exporting and re-importing the MOF file would not create duplicates. However, the Host Integration Server WMI provider allows pool-to-workstation association instances to be duplicated because, by design, duplicates of this type of object are allowed. You can associate the same pool to the same workstation or user multiple times. This is used by emulators to create more sessions for clients. Therefore, you cannot identify one such association from another. The WMISNA provider, WMISNA.DLL, always creates new associations of these types, even if an association with the same pair (Pool, Wks) already exists. This object type is allowed only in this specific case. However, this can create a problem for applications developed using WMI (the Import/Export sample, for example) if the application does not know not to create the duplicates.  
  
 The follow sequence illustrates this issue using the ImportExport sample:  
  
1. Use SNA Manager to create a pool workstation association.  
  
2. Export the SNA configuration to a MOF file using the ImportExport utility.  
  
3. Import that same MOF file again using the ImportExport utility.  
  
4. Duplicate pool-workstation associations are created.  
  
   The result is that if a client uses the import/export sample or a similar application developed using WMI on a Host Integration Server configuration that has pool-to-workstation associations, then the number of associations will effectively double after running the sample. The workaround using the ImportExport sample would be as follows:  
  
5. Export the configuration to a MOF file.  
  
6. Remove the pool to workstation associations from the MOF file that was just created.  
  
7. Re-import the MOF file.  
  
   When importing the configuration from one domain to another using the ImportExport sample or a similar application developed using WMI, then step 2 should be ignored. Typically, WMI applications should copy an existing configuration to a blank configuration file so this condition does not occur.
