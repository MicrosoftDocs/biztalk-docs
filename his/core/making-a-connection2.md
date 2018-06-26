---
title: "Make a connection | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 484ef761-830a-4c5b-bc1c-235ec9044a3f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Making a Connection
Give users and groups access to the mainframe environment, install connections, and verify the installation. For information on the IP-DLC Link Service, see [IP-DLC Link Service](./ip-dlc-link-service2.md).
  
## Install HIS
  
- Verify Host connection information.  
  
- Verify Windows Server configuration information.  
  
- Verify Host Integration Server SNA service configuration information  
  
- Install [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
- Install appropriate link services.  
  
## Configure HIS
  
-   [Step 1 (L) Creating and Configuring Link Services](../core/step-1-l-creating-and-configuring-link-services1.md)  
  
-   [Step 2 (C) Creating and Configuring Connections](../core/step-2-c-creating-and-configuring-connections1.md)  
  
-   [Step 3 (LU) Creating and Configuring 3270 LUs](../core/step-3-lu-creating-and-configuring-3270-lus1.md)  
  
-   [Step 4 (A) Adding and Assigning Users](../core/step-4-a-adding-and-assigning-users1.md)  
  
## Test HIS
  
-   [Testing Connections with the 3270 Client](../core/testing-connections-with-the-3270-client2.md)  
  
-   [Testing Connections with the 5250 Client](../core/testing-connections-with-the-5250-client2.md)  

## Things to consider
For a connection to be established successfully, a number of software settings and hardware characteristics must work together. The following table outlines items to consider when configuring a connection with [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
|Element|Considerations|  
|-------------|--------------------|  
|**Host configuration** settings must match the connectionandserversettings on the Host Integration Server computer.|**Mainframe node ID settings**: For most mainframes, IDBLK and IDNUM in the physical unit (PU) definition must match the two parts of the Remote Node ID on the Host Integration Server connection.<br /><br /> **AS/400 name settings**: For the AS/400 computer, local and remote control point names (CP names) and network names must be matched with corresponding Host Integration Server settings<br /><br /> **Addresses**: For 802.2, X.25, or channel connections, you must match the host settings with equivalent settings on the Host Integration Server connection.<br /><br /> **BTU length**: For the mainframe, the BTU length is set through MAXDATA in the PU definition. For the AS/400 computer, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.<br /><br /> **Other settings**: With SDLC, the NRZ/NRZI settings on the host must match those on the Host Integration Server connection.|  
|**For SDLC and X.25**<br /><br /> **Communications hardware**: line, modem (if applicable), and adapter characteristics must match thelink serviceandconnectionsettings on the Host Integration Server computer.|**Speed and duplexing**: For SDLC and X.25, note the speed and duplexing capabilities of the line, modem (or DCE), and adapter, to be sure that they will not be exceeded by the settings in the Host Integration Server link service and connection. Settings for fast transmission or for full duplexing cause greater demands on hardware. The hardware element with the smallest capacity limits the capacity of the entire system.|  
  
## More good stuff
[IP-DLC Link Service](./ip-dlc-link-service2.md)  