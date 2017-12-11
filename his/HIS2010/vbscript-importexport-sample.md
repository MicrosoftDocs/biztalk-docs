---
title: "VBScript ImportExport Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87f5aa2c-d78f-4512-831d-373cd1e06854
caps.latest.revision: 3
---
# VBScript ImportExport Sample
The Administration\VBScript folder contains a sample written in Microsoft Visual Basic Scripting Edition (VBScript) that illustrates how to import and export SNA configuration information from [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] in managed object format (MOF) using Windows Management Instrumentation (WMI). This sample relies on the MOFCOMP.exe application supplied with Microsoft Windows for importing.  
  
 In the following examples, ImportExport.VBS has been renamed to HISCFG.vbs.  
  
 The usage for this command-line tool for exporting configuration information is as follows:  
  
```  
HISCFG [/S:server] [/N:namespace] [/C:class] [/O:outfile]   
       [/U:username] [/W:password] [/Q]  
```  
  
 The various command-line options are explained in the following table.  
  
> [!NOTE]
>  Case is ignored for command-line options except for help and either the '/' or '-' character is interpreted as the leading character for an option. The following table uses the '/' character for illustration.  
  
|Command-Line Switch|Comments|  
|--------------------------|--------------|  
|**/?**|This flag shows the usage for this command and exits.|  
|**/C**|The name of the WMI parent class to be queried. This should be set to one of the WMI classes defined in the MOF files supplied with [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].<br /><br /> This parameter defaults to *MsSna_Config* and exports all of the classes SNA classes and their associations.|  
|**/h**|This flag shows the usage for this command and exits.|  
|**/N**|The WMI namespace to be queried. This parameter defaults to "root\MicrosoftHIS" for [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].|  
|**/O**|The name of the file used for output. This parameter has no default value.|  
|**/Q**|This Boolean flag indicates whether this is query should be completed quietly without displaying any status or error messages. This parameter defaults to verbose option.|  
|**/S**|The name of the computer running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. This parameter has no default value.|  
|**/U**|The user name of a user on the domain or active directory where [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] is running with administrative rights. This parameter has no default value.|  
|**/W**|The password of a user on the domain or active directory where [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] is running with administrative rights. This parameter has no default value.|  
  
 The usage for this command-line tool for importing SNA configuration information is as follows:  
  
```  
HISCFG [/I:inputfilename]  
```  
  
 A potential problem using WMI can occur with duplicate logical unit (LU) pools that can be illustrated using this sample program. Normally, exporting and re-importing the MOF file would not create duplicates. However, the HIS WMI provider allows pool-to-workstation association instances to be duplicated because, by design, duplicates of this type of object are allowed. It is possible to associate the same pool to the same workstation or user multiple times. Emulators use this to create more sessions for clients. Therefore, it is not possible to identify one such association from another. The WMISNA Provider, WMISNA.DLL, always create new associations of these types, even if an association with the same pair (Pool, Wks) already exists. Only in the case of this object type is this allowed. However, this can create a problem for applications developed using WMI (the Import/Export sample, for example) if the application does not know to not create the duplicates.  
  
 The following sequence illustrates this issue using the ImportExport sample:  
  
1.  Create a Pool-Workstation association by using Host Integration Server Manager or the Administration Manager client.  
  
2.  Export the SNA configuration to a MOF file using the ImportExport utility.  
  
3.  Import that same MOF file again using the ImportExport utility.  
  
4.  Duplicate Pool-Workstation associations will be created.  
  
 The result is that if a client uses the import/export sample or a similar application developed using WMI on a [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] configuration that has pool-to-workstation associations, then the number of associations will effectively double after running the sample. The workaround using the ImportExport sample would be as follows:  
  
1.  Export the configuration to a MOF file.  
  
2.  Remove the pool to workstation associations from the MOF file just created.  
  
3.  Import the MOF file back.  
  
 When importing the configuration from one domain to another using the ImportExport sample or a similar application developed using WMI, then step 2 should be ignored. Normally, WMI applications should copy an existing configuration to a blank configuration file so this condition does not arise.  
  
## See Also  
 [Administration and Management Samples](../HIS2010/administration-and-management-samples.md)