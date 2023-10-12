---
description: "Learn more about: Metadata Errors"
title: "Metadata Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Metadata Errors
Information for diagnosing and resolving WCF Metadata errors.  
  
## Error consuming WCF service metadata

| Field | Error Details|
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                        Error consuming WCF service metadata                        |
  
### Explanation  
 This error indicates the metadata for the service is either not available or is not valid.  
  
### User Action  
 Correct the service metadata and try to consume (if you own the WCF service you are trying to consume). Go to the Service Configuration Editor (**svcConfigEditor.exe**) and make changes to the configuration file.  Otherwise, contact the service provider

## Failed to get metadata

| Field | Error Details|
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                          Failed to get metadata from "{0}                          |
  
## Explanation  
 This error indicates the metadata is not available for that service.  
  
## User Action  
 Enable metadata for the service and run the consuming wizard again (if you own the WCF service you are trying to consume). Otherwise, contact the service provider.
