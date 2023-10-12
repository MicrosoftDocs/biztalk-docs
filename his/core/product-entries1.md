---
description: "Learn more about: Product Entries"
title: "Product Entries1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Product Entries
All of the information relevant to the product as a whole resides in the registry under the key **SOFTWARE\Microsoft**. Each product or link support has an entry whose name consists of the product name and version separated by an underscore. This key contains most of the information about the product, such as the script name and option name that control it and the service name for that particular instance.  
  
 Each instance key must also have a NetRules key. This key contains all of the information for the Network Control Panel Applet bindings.  
  
 The Host Integration Server Setup writes the path of the root directory of the computer's Host Integration Server tree into the key:  
  
 **SOFTWARE\Microsoft\SNA Server\CurrentVersion\Setup\RootDir**
