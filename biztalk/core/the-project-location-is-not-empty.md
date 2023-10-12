---
description: "Learn more about: The project location is not empty"
title: "The project location is not empty"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The project location is not empty
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                 |
| Product Version |                                                                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                             |
|    Event ID     |                                                                                                                         0                                                                                                                          |
|  Event Source   |                                                                                                                         0                                                                                                                          |
|    Component    |                                                                                                                         0                                                                                                                          |
|  Symbolic Name  |                                                                                                                         0                                                                                                                          |
|  Message Text   | The project location "{0}" is not empty. You need to do one of the following: 1. Choose a different location for the new project, 2. Specify overwrite to reuse the existing location, or 3. Manually delete the contents of the project location. |
  
## Explanation  
 This error indicates the virtual directory where the service is trying to be published is not empty.  
  
## User Action  
 Select the overwrite location to reuse the same location. Or specify a new location.  In the WCF Service Publishing Wizard, select **Overwrite Existing Location** and click **Next**. This step overwrites the location.
