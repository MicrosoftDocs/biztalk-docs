---
description: "Learn more about: A file not found exception occurred while reflecting a BizTalk assembly"
title: "A file not found exception occurred while reflecting a BizTalk assembly"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# A file not found exception occurred while reflecting a BizTalk assembly
## Details  

|  Parameter |  Value  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                           |
| Product Version |                                                                                                                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                       |
|    Event ID     |                                                                                                                                                                   0                                                                                                                                                                    |
|  Event Source   |                                                                                                                                                                   0                                                                                                                                                                    |
|    Component    |                                                                                                                                                                   0                                                                                                                                                                    |
|  Symbolic Name  |                                                                                                                                                                   0                                                                                                                                                                    |
|  Message Text   | A file not found exception occurred while reflecting BizTalk assembly "{0}". This problem may occur if one or more dependencies are not available. To correct this problem, try one of the following: 1. Copy the dependencies of the assembly to the same folder. 2. Install the missing dependencies into the Global Assembly Cache. |

## Explanation  
 This error indicates the BizTalk Assembly that is being published references another assembly that is not in the Global Assembly Cache (GAC) or in the same directory.  

## User Action  
 In addition to the actions specified in the error message, move the reference assembly to the Global Assembly Cache or copy it to the same location as the BizTalk assembly  

1. Click **Start**, point to **All Programs**, point to **Visual Studio**, and then click **Visual Studio**.  

2. Open a command prompt.  

3. Browse to the location of the assembly, and enter **gacutil /I /\<**<em>assembly name</em>**\>.dll**
