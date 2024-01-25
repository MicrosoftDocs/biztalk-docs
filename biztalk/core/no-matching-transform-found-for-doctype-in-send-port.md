---
description: "Learn more about: No matching transform found for DocType in Send Port"
title: "No matching transform found for DocType in Send Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# No matching transform found for DocType in Send Port
## Details  
  
| Field | Error Details|
|-----------------|--------------------------------------------------------------------------------------------------------|
|  Product Name   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| Product Version |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    Event ID     |                                                   -                                                    |
|  Event Source   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    Component    |                                               EDI Engine                                               |
|  Symbolic Name  |                             NoMatchingTransformFoundForSendPortAndDocType                              |
|  Message Text   | No matching transform found for DocType {0} in Send Port {1}. Inconsistent with ExplorerOM information |
  
## Explanation  
 This error indicates that a matching transform was not found for a given DocType and SendPort.  
  
## User Action  
 To resolve this error, proceed as follows:  
  
1.  Open the BizTalk Administration console, locate the transport, and right-click the transport name.  
  
2.  Click **Properties**.  
  
3.  In the port Type list, select the correct port. Click **Configure**.  
  
4.  In the [port name] Send Port Properties dialog box, click **Outbound Maps** in the left pane.  
  
5.  Verify that the map is listed here and that it corresponds to the correct document type.
