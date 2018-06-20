---
title: "Unable to get binding type for binding extension | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7cfc81-7439-48f9-8cac-42b2419ecd9d
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unable to get binding type for binding extension
## Details  

|                 |                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                        |
| Product Version |                                                                                    [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                    |
|    Event ID     |                                                                                                                0                                                                                                                 |
|  Event Source   |                                                                                                                0                                                                                                                 |
|    Component    |                                                                                                                0                                                                                                                 |
|  Symbolic Name  |                                                                                                                0                                                                                                                 |
|  Message Text   | Unable to get binding type for binding extension "{0}". If machine.config was updated while your application was open, restart your application to pick up changes. Verify the binding extension is registered in machine.config |

## Explanation  
 A custom binding extension for a WCF-Custom or a WCF-CustomIsolated transport was not configured properly.  

## User Action  
 To resolve this error do one or more of the following:  

- Ensure the **machine.config file** in **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** has the \<**bindingExtensions**\> element configured properly.  

- In Windows Explorer, go to **%WinDir%\Assembly**, and make sure the assemblies implementing the custom binding extension are installed properly.  

- For the WCF-Custom adapter, in the BizTalk Administration console, restart the host instance running the WCF transport.  

- For the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool hosting the WCF transport.  

- Open and close the BizTalk Administration console if it was opened  

  For further information, see the following resource:  

- [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)
