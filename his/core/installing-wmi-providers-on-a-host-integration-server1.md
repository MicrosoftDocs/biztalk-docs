---
description: "Learn more about: Installing WMI Providers on a Host Integration Server"
title: "Installing WMI Providers on a Host Integration Server1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing WMI Providers on a Host Integration Server
Microsoft Host Integration Server provides several Windows Management Instrumentation (WMI) providers. The managed object format (MOF) files used by Host Integration Server are installed in the System directory below where Host Integration Server is installed. The default location for these files is in the following subdirectory:  
  
 C:\Program Files\Microsoft Host Integration Server 2013\System  
  
 To use or view these MOF files on other computers (a computer with the Administration client or end-user client, for example) to develop applications, these MOF files must be copied from the Host Integration Server computer. These MOF files document the WMI providers supplied with Host Integration Server and the class identifiers (CLSIDs), classes, properties, and methods supported by these providers.
