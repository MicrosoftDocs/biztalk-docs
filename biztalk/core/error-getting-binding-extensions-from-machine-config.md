---
title: "Error getting binding extensions from machine.config | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error getting binding extensions from machine.config
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                Error getting binding extensions from machine.config                |
  
## Explanation  
 This error occurs when a  receive location or send port binding configuration has a user defined binding extension, but it is not defined in machine.config file. This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.  
  
## User Action  
 Define the binding extension used in the receive location or send port in machine.config file. Also, to get a custom behavior or binding element to work with WCF-Custom adapter, complete these steps:  
  
1.  GAC the assembly  
  
2.  Modify your machine.config file (found in **%FrameworkDir%\v4.0.30319\CONFIG**).  
  
    1.  Load your behavior DLL inside the Service Configuration Editor (**svcConfigEditor.exe**).  
  
    2.  Save the configuration to an **app.config** file  
  
    3.  Copy and paste the **system.servicemodel** extensions section in a similar section in machine.config. If **system.servicemodel** section is not present in machine.config, your must create one. The following is an example from the configuration section of a machine.config file:  
  
        ```  
          <system.serviceModel>  
            <extensions>  
              <behaviorExtensions>  
                <add name="BizTalkWcfContractNamespaceTestServiceBehaviorExtension" type="ASB.BizTalk.Samples.BizTalkWcfContractNamespaceTestServiceBehaviorExtension, CustomBizTalkWcfBehaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=7631521c07cf34b4" />  
              </behaviorExtensions>  
            </extensions>  
          </system.serviceModel>  
        ```  
  
> [!NOTE]
>  The above code can also be added to the WCF Extensions tab. If the extension needs to be on the receive side, see the **\<Host Name\> Properties Dialog Box, WCF Extensions** tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. If the extension needs to be on the send side, see **\<Host Name\> Properties Dialog Box, WCF Extensions** tab (WCF-Custom Adapter Send Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 3. Close and reopen your admin console. You should be able to see your custom behavior in the WCF-Custom adapter, and the port should stay enabled when you enable it.