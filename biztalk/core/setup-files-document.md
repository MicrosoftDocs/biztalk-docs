---
title: "SetUp-Files Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, SetUp-File document"
ms.assetid: f2f11033-e85e-4293-80b2-9870bb23eafd
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SetUp-Files Document
The SetUp-Files document contains information about the names and locations of the data files to import. It has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Setup-Files>  
    <App_Type_file>c:\ListOfAppType.xml</App_Type_file>  
    <App_Instance_file>c:\ListOfAppInstance.xml</App_Instance_file>  
    <IDXRef_file>c:\ListOfIDXRef.xml</IDXRef_file>  
    <IDXRef_Data_file>c:\ListOfIDXRefData.xml</IDXRef_Data_file>  
    <ValueXRef_file>c:\ListOfValueXRef.xml</ValueXRef_file>  
    <ValueXRef_Data_file>c:\ListOfValueXRef_Data.xml</ValueXRef_Data_file>  
    <Msg_Def_file>c:\ListOfMessageDefinition.xml</Msg_Def_file>  
    <Msg_Text_file>c:\ListOfMessageText.xml</Msg_Text_file>  
</Setup-Files>  
  
```  
  
 The following table describes each element and its contents:  
  
|Element|Description|  
|-------------|-----------------|  
|App_Type_file|Path and name of the file containing the **listOfAppType** document. For more information, see [listOfAppType Document](../core/listofapptype-document.md) document.|  
|App_Instance_file|Path and name of the file containing the **listOfAppInstance** document. For more information, see [listOfAppInstance Document](../core/listofappinstance-document.md) document.|  
|IDXRef_file|Path and name of the file containing the **listOfIDXRef** document. For more information, see [listOfIDXRef Document](../core/listofidxref-document.md) document.|  
|IDXRef_Data_file|Path and name of the file containing the **listOfIDXRefData** document. For more information, see [listOfIDXRefData Document](../core/listofidxrefdata-document.md) document.|  
|ValueXRef_file|Path and name of the file containing the **listOfValueXRef** document. For more information, see [listOfValueXRef Document](../core/listofvaluexref-document.md) document.|  
|ValueXRef_Data_file|Path and name of the file containing the **listOfValueXRefData** document. For more information, see [listOfValueXRefData Document](../core/listofvaluexrefdata-document.md) document.|  
|Msg_Def_file|Path and name of the file containing the **listOfMessageDef** document. For more information, see [listOfMessageDef Document](../core/listofmessagedef-document.md) document.|  
|Msg_Text_file|Path and name of the file containing the **listOfMessageText** document. For more information, see [listOfMessageText Document](../core/listofmessagetext-document.md) document.|  
  
 You may give the files any names you choose. However, each of the files must contain the XML document of the indicated type.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)