---
description: "Learn more about: Error loading assembly"
title: "Error loading assembly"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error loading assembly
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                                          |
| Product Version |                                                                                                                                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                                      |
|    Event ID     |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  Event Source   |                                                                                                                                                                                  0                                                                                                                                                                                   |
|    Component    |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  Symbolic Name  |                                                                                                                                                                                  0                                                                                                                                                                                   |
|  Message Text   | This error indicates the location may not be fully trusted if it is on a network share. Check the Code Access Security policy for the Zone. Or the file may not be a BizTalk .NET assembly. Check the assembly for the [assembly: BizTalkAssembly] custom attribute. Or the file may not be a .NET assembly. If the file is a .dll or  exe, it may be unmanaged code |
  
## Explanation  
 This error indicates the location may not be fully trusted if it is on a network share. Check the Code Access Security policy for the Zone. Or the file may not be a BizTalk .NET assembly. Check the assembly for the [*assembly: BizTalkAssembly*] custom attribute. Or the file may not be a .NET assembly. If the file is a .dll or  exe, it may be unmanaged code.  
  
## User Action  
 Grant Full trust level to the location if it’s from a reliable source.  Ensure the dll is a valid BizTalk .net assembly.
