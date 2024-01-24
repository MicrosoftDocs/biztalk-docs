---
description: "Learn more about: Making a Connection"
title: "Make a connection"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
|**Host configuration** settings must match the connectionandserversettings on the Host Integration Server computer.|**Mainframe node ID settings**: For most mainframes, IDBLK and IDNUM in the physical unit (PU) definition must match the two parts of the Remote Node ID on the Host Integration Server connection.<br /><br /> **IBM System i name settings**: For the IBM System i computer, local and remote control point names (CP names) and network names must be matched with corresponding Host Integration Server settings<br /><br /> **BTU length**: For the mainframe, the BTU length is set through MAXDATA in the PU definition. For the IBM System i computer, this is set through MAXFRAME. These should equal the Max BTU Length on the Host Integration Server connection.<br /><br />|  
  
  
## More good stuff
[IP-DLC Link Service](./ip-dlc-link-service2.md)  
