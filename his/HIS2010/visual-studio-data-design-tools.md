---
title: "Visual Studio Data Design Tools | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d14674d5-a1c6-45b6-bd9e-cad95c890586
caps.latest.revision: 3
---
# Visual Studio Data Design Tools
This topic contains the following sections:  
  
 [OLE DB Provider for AS/400 and VSAM](../HIS2010/visual-studio-data-design-tools.md#ole)  
  
##  <a name="ole"></a> OLE DB Provider for AS/400 and VSAM  
 When using Visual Studio, it is possible to get the following error when accessing the OLE DB Provider for AS/400 and VSAM:  
  
```  
"File is in use by another process. Unspecified error"  
```  
  
 This error can occur after a data source has been configured for the OLE DB Provider for AS/400 and VSAM using the Data Links property page and a command is added using Visual Studio where the command added is the following:  
  
```  
"EXEC OPEN filename"  
```  
  
 Using Visual Studio query builder and selecting Run for this command can result in the preceding error. The query builder is opening the file and then trying to open it a second time based on the command to execute without closing the first copy. Depending upon the share options of the data set and the DBPROP_INIT_MODE property set for this data source, this error can occur and the user can be locked out of the host file.  
  
## See Also  
 [Data Integration (Troubleshooting)](../HIS2010/data-integration-troubleshooting-1.md)