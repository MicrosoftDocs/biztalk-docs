---
title: "ExportParties Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b421c8ed-d505-48ba-9d1d-8519c9d51750
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ExportParties Command
Exports all the parties and agreements to an XML bindings file.

> [!IMPORTANT]
> This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.

## Usage
  **BTSTask ExportParties -Destination**:*value* [**-Server**:*value*] [**-Database**:*value*]
  
## Parameters

|Parameter|Required|Value|  
|---|---|---|  
| **-Destination** | Required | Path and file name of the XML binding file to write. |
| **-Server** | Optional | The name of SQL server hosting the BizTalk configuration database. |
| **-Database** | Optional | The name of the BizTalk configuration database.|

## Sample
  `ExportParties  -Destination:"C:\Temp\MyParties.Xml"` 

## Remarks
  Only parties, agreements, and EDI fallback settings are exported. No application artifacts are exported.
