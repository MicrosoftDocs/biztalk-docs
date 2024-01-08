---
description: "Learn more about: Logical Unit (LU)"
title: "Logical Unit (LU)1"
ms.custom: ""
ms.date: "12/13/2023"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Logical Unit (LU)
A logical unit (LU) is a configurable unit of software that contains the information needed to specify the type of communications session with the host computer or peer system. Thus, an LU is a point of access to the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] network. There are several types of LUs:  
  
- APPC  
  
- 3270  
  
- Logical unit application (LUA)  
  
  LUs represent a set of functions that manage the exchange of data between users and applications, acting as intermediaries between the user and the network. Host Integration Server protocols identify several LUs on host computers that represent specific functions. The following table is a list of LU numbers and a brief functional description.  
  
|                     LU number                     |                                                                                                                                                                                      Description                                                                                                                                                                                      |
|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| LU 0 (also LU/A or LUA, logical unit application) |                                                                                                                  General purpose LU for development of specialized applications such as TN3270. Used for program-to-program communications in hierarchical networks.                                                                                                                  |
|                       LU 1                        | LU 1 handles the transmission of printer data to network and system printers in SNA character string format.<br /><br /> IBM 3287-type printers and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Host Print service that allows you to redirect print data streams to LAN printers.<br /><br /> Used to communicate with multiple-device terminals. |
|                       LU 2                        |                                                                                                                          IBM monochrome terminals 3278 (3270)<br /><br /> IBM Color graphic terminals 3279/3179<br /><br /> Host Integration Server displays                                                                                                                          |
|                       LU 3                        |                                    IBM 3284-style printers and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Host Print service, which allows you to redirect print data streams to LAN printers. LU 3 is a simple printing protocol that uses the 3270 data stream format to communicate with a single printer.                                     |
|                       LU 4                        |                                                                                                                                                IBM 6670 information distributor and is not supported through Host Integration Server.                                                                                                                                                 |
|                       LU 5                        |                                                                                                                                                                                     Not defined.                                                                                                                                                                                      |
|                       LU 6                        |                                                    LU 6.2 is most common revision. IBM 5250 devices and Host Integration Server local and remote APPC LUs.<br /><br /> Provides peer-to-peer communication through Advanced Program-to-Program Communication (APPC) and (Common Programming Interface for Communications (CPI-C).                                                     |
|                       LU 7                        |                                                                                                                                                    IBM 5250 display terminal. Used mainly on System 3.x but not on IBM i systems.                                                                                                                                                    |
  
 On Host Integration Server computers, you can configure LUs to emulate the 3270 data streams needed to communicate with the mainframes or 5250 data streams for IBM i systems.  
  
 A 3270 LU is a dependent LU that requires the mainframe to function. It has a fixed designation, such as a display LU, printer LU, logical unit application (LUA) LU, or downstream LU. Each type of LU has a specific number assigned to it. A 3270 LU on Host Integration Server has an LU number, and a corresponding resource must be defined on the host computer. The 3270 LU name is arbitrary and does not have to match the name of the resource on the host.  
  
 Additional information about APPC is available later in this section.  
  
## See Also  
 [SNA Service](../core/sna-service2.md)
