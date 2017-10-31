---
title: "Return Value Positioning1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7d9b6f1-979f-4b09-9775-383ebdefb6b8
caps.latest.revision: 3
---
# Return Value Positioning
When an Automation method returns control to the calling application, it can return data as the method's value (as distinct from returning data as an output parameter). However, there is no analogous concept when you are dealing with a COBOL or Report Program Generator (RPG) data declaration.  
  
 Transaction Integrator (TI) allows you to select one of the data description entries in a data declaration that will be returned to the calling application. When you select an entry as the return value and that entry is not the first entry in the data declaration, the return value is said to be positioned after the parameters.  
  
 You can use this feature, for example, when your data declaration describes a table and you need to return a recordset on the Automation side. For example, if you are using Remote Data Service (RDS) to bind to a grid control for a Web application, your Automation method must return the recordset rather than define a parameter that represents an output recordset.  
  
 When you import host definitions, the Import COBOLor Import RPG Wizard provides a step that allows you to select data description entries as return values. If you are manually creating a method and you want the method's return value to be placed in a location other than at the front of the data declaration, you can specify the location on the **Advanced** tab of the method properties. Use the **Position return value after the parameter** drop-down list.