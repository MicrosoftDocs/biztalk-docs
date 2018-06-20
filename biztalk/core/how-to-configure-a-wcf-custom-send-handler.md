---
title: "How to Configure a WCF-Custom Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00758b87-dffb-488b-9cf3-564d0ccd5938
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-Custom Send Handler
You must configure the send handler properties if you want the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] to look up the custom behavior extensions from locations other than machine.config.  
  
## Why Should WCF-Custom Adapter Look up Custom Behavior Extensions from Locations Other than machine.config?  
 Custom behavior extensions used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is registered in the machine.config. Before loading the behavior extensions, the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] looks for the behavior extensions in machine.config. However, machine.config is ideally used to store configuration information that is required across all applications running on a particular computer. On the other hand, WCF custom behavior extensions may be required only by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and not by all the applications running on the computer. So, while storing the custom behavior extensions in machine.config serves the purpose, it is not the most optimal location.  
  
 With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the adapter handler properties provide an additional location from which the [!INCLUDE[wcfadapter_short](../includes/wcfadapter-short-md.md)] can look up the custom behavior extensions. Note that this does not replace the behavior extensions already available in machine.config.  
  
### Additional Considerations  
 Keep the following points in mind while configuring the WCF-Custom send handler properties:  
  
-   The custom behavior extensions must be available either in the machine.config or in the adapter handler properties. The custom behavior extensions must not be duplicated at both locations.  
  
-   If the custom behavior extension is already available in the machine.config and you try to set the same behavior extension for the adapter handler properties, you get an error as soon as you try to set the property.  
  
-   If the custom behavior extension is already set for the adapter handler properties and you then update the machine.config with the same behavior extension, you will get a runtime error and it is also logged in the event log.  
  
-   The assemblies referred in the custom behavior extension must be present in the Global Assembly Cache (GAC) before you set the adapter handler properties.  
  
## Configuring the Adapter Handler Properties  
 Use the procedure in this topic to configure a WCF-Custom send handler.  
  
#### To configure the adapter handler properties  
  
1. In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2. In the expanded adapter list, click **WCF-Custom**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  
  
3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.  
  
4. In the **WCF-Custom Transport Properties** dialog box, on the **WCF Extensions** tab, do the following:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Import**|Imports a WCF configuration file with WCF custom behavior extensions. Clicking this button opens the **Import WCF configuration** dialog box to browse and locate a WCF configuration file. Note that the file should be a valid WCF configuration file. For more information about WCF configuration schema, see “Windows Communication Foundation Configuration Schema” at [http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953).|  
   |**Export**|Exports the WCF custom behavior extension to a WCF configuration file. Clicking this button opens the **Export WCF configuration** dialog box to browse and save the WCF configuration file.|  
   |**Clear**|Clears the existing WCF custom behavior extension from the adapter handler properties.|  
  
## See Also  
 [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)