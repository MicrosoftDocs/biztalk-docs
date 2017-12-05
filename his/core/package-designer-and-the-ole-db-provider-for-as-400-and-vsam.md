---
title: "Package Designer and the OLE DB Provider for AS-400 and VSAM | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bf9791d-376b-4f74-8e5a-29c2910ddc27
caps.latest.revision: 7
---
# Package Designer and the OLE DB Provider for AS-400 and VSAM
The OLE DB Provider for AS/400 and VSAM supports SQL Server Integration Services (SSIS), with the following limitations:  
  
1.  Only bulk table copy (Import/Export) is available.  
  
2.  Only one data conversion layout (HCD map) per dataset. Specifically, there is no support for converting nested records, such as COBOL OCCURS or REDEFINE, or RPG overlay.  
  
 When using SQL Server Integration Services with the Microsoft OLE DB Provider for AS/400 and VSAM within the Package Designer in Visual Studio, SSIS may raise the following warning dialog:  
  
 `Warning at {9C6AC00C-13CF-4EF8-B44A-72055CC508C2} [OLE DB Source [262]]: Cannot retrieve the column code page info from the OLE DB provider.  If the component supports the "DefaultCodePage" property, the code page from that property will be used.  Change the value of the property if the current string code page values are incorrect.  If the component does not support the property, the code page from the component's locale ID will be used.`  
  
 Server Integration Services supports the option of specifying a per-column Locale Identifier for string data types, such as CHARACTER. However, the Microsoft OLE DB Provider for AS/400 and VSAM does not support this option. You can work around this limitation by modifying the settings in the Advanced Editor.  
  
### To allow the OLE DB Provider for AS/400 and VSAM to use the default code page  
  
1.  In the Data Flow Task Design surface, add a new OLE DB Source or OLE DB Destination for use with the Microsoft OLE DB Provider for AS/400 and VSAM.  
  
2.  Right-click the OLE DB source or destination object, and then click **Show Advanced Editor…**.  
  
3.  On the Advanced Editor screen, click the Component Properties page.  
  
4.  Set **AlwaysUseDefaultCodePage** to True.  
  
5.  Click **OK**.  
  
     Clicking OK saves the settings for use with the current OLE DB source or destination object within the SSIS package.  
  
## See Also  
 [OLE DB Provider for AS-400 and VSAM Programmer's Guide](../core/ole-db-provider-for-as-400-and-vsam-programmer-s-guide.md)