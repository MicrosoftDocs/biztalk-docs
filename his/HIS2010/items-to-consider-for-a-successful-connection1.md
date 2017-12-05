---
title: "Items to Consider for a Successful Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27467d96-1629-4e2b-85ae-4713493d9265
caps.latest.revision: 3
---
# Items to Consider for a Successful Connection
For a connection to be established successfully, a number of software settings and hardware characteristics must work together.  
  
 The following table outlines items to consider when configuring a connection with [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 For information on the new IP-DLC Link Service, see [IP-DLC Link Service](../HIS2010/ip-dlc-link-service1.md).  
  
|Element|Considerations|  
|-------------|--------------------|  
|**Host configuration** settings must match the connectionandserversettings on the Host Integration Server computer.|**Mainframe node ID settings**: For most mainframes, IDBLK and IDNUM in the physical unit (PU) definition must match the two parts of the Remote Node ID on the Host Integration Server connection.<br /><br /> **AS/400 name settings**: For the AS/400 computer, local and remote control point names (CP names) and network names must be matched with corresponding Host Integration Server settings<br /><br /> **Addresses**: For 802.2, X.25, or channel connections, you must match the host settings with equivalent settings on the Host Integration Server connection.<br /><br /> **BTU length**: For the mainframe, the BTU length is set through MAXDATA in the PU definition. For the AS/400 computer, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.<br /><br /> **Other settings**: With SDLC, the NRZ/NRZI settings on the host must match those on the Host Integration Server connection.|  
|**For SDLC and X.25**<br /><br /> **Communications hardware**: line, modem (if applicable), and adapter characteristics must match thelink serviceandconnectionsettings on the Host Integration Server computer.|**Speed and duplexing**: For SDLC and X.25, note the speed and duplexing capabilities of the line, modem (or DCE), and adapter, to be sure that they will not be exceeded by the settings in the Host Integration Server link service and connection. Settings for fast transmission or for full duplexing cause greater demands on hardware. The hardware element with the smallest capacity limits the capacity of the entire system.|  
  
## See Also  
 [Important Connection Information](../HIS2010/important-connection-information1.md)