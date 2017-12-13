---
title: "Product Entries1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b025f6-f80b-451f-bef9-dfca7e698e4a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Product Entries
All of the information relevant to the product as a whole resides in the registry under the key **SOFTWARE\Microsoft**. Each product or link support has an entry whose name consists of the product name and version separated by an underscore. This key contains most of the information about the product, such as the script name and option name that control it and the service name for that particular instance.  
  
 Each instance key must also have a NetRules key. This key contains all of the information for the Network Control Panel Applet bindings.  
  
 The Host Integration Server Setup writes the path of the root directory of the computer's Host Integration Server tree into the key:  
  
 **SOFTWARE\Microsoft\SNA Server\CurrentVersion\Setup\RootDir**