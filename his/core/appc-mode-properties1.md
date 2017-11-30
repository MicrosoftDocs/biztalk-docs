---
title: "APPC Mode Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Mode"
ms.assetid: 9b7f1a4e-c8bd-41a7-a447-c0e258b13ed6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# APPC Mode Properties
The following tabs are available on the APPC Mode Properties Sheet:  
  
## APPC Mode Properties: General  
 **Mode Name**  
 Enter a Mode Name.  
  
 **Comment**  
 Optionally, type a comment of not more than 25 characters.  
  
## APPC Mode Properties: Limits  
 **Parallel Session Limit**  
 Specify the maximum number of sessions allowed with this mode. To allow only a single session, specify 1. To allow parallel sessions, specify a value greater than 1. If the local APPC LU to be used with this mode is dependent, specify 1; dependent local APPC LUs cannot have parallel sessions. One of the key mode properties is the **Parallel Session Limit**. This limit determines whether an LU-LU pair can carry on only one interaction at a time (a parallel session limit of 1), or multiple concurrent interactions (a parallel session limit greater than 1). If parallel sessions are to be allowed with an LU-LU pair, the local LU must be independent, and the remote LU in the pair must support parallel sessions.  
  
 If the LU-LU pair can carry on multiple parallel sessions, other mode properties, such as minimum contention winner limit, determine to what extent each LU can initiate interactions.  
  
 **Minimum Contention Winner Limit**  
 Specify the Minimum Contention Winner Limit. The sum of the Minimum Contention Winner Limit and the Partner Min Contention Winner Limit must be less than or equal to the Parallel Session Limit.  
  
 **Partner Min Contention Winner Limit**  
 Specify the Partner Min Contention Winner Limit. The sum of the Partner Min Contention Winner Limit and the Minimum Contention Winner Limit must be less than or equal to the Parallel Session Limit.  
  
 **Automatic Activation Limit**  
 Specify the number of contention winner sessions to be activated for the local LU whenever the connection for this mode is started. In a local contention winner session, the local LU can initiate conversations without permission from the partner LU.  
  
 This does not apply for single-system APPC (communication between two local LUs on the same system).  
  
## APPC Mode Properties: Characteristics  
 **Pacing Send Count**  
 Specify the maximum number of frames for the local LU to send without an SNA pacing response from the partner LU. If you specify 0, the local LU can send an unlimited number of frames without receiving a response; in this case, the partner LU can negotiate and set a limit on the count.  
  
 **Pacing Receive Count**  
 Specify the maximum number of frames for the local LU to receive from the partner LU before the local LU sends an SNA pacing response. If you specify 0, the local LU can receive an unlimited number of frames without sending a response.  
  
 **Max Send RU Size**  
 Specify the maximum size for RUs sent by the TP(s) on the local system.  
  
 It is not necessary to set a minimum send RU size, which is 256 on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 **Max Receive RU Size**  
 Specify the maximum size for RUs received from the TP(s) on the remote system.  
  
 It is not necessary to set a minimum receive RU size, which is 256 on [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 **High-Priority Mode**  
 Select to give preference to communication with this mode over communication with a low-priority mode.  
  
## APPC Mode Properties: Partners  
 This tab allows you to **Add** or **Remove** APPC LU partnerships from the Host Integration Server configuration file. The mode name appears in the title. The list box shows the **Server**, **Local LU Alias**, **Remote LU Alias**, **Connection**, and which LUs are partnered with the APPC mode in the title.  
  
 **Remove**  
 Click **Remove** to delete APPC LU partnerships from the Host Integration Server configuration file.  
  
#### Add  
  
1.  Click **Add** to add APPC LU partnerships from the Host Integration Server configuration file. The **Add Partnerships** dialog box appears.  
  
2.  Select a **Server name** from the subdomain by clicking the DOWN arrow in the drop down list.  
  
3.  After the server is selected, a list box showing **Local LU**s and a list box showing **Partner LU** and **Connection** are filled. Make selections from each list to establish partnerships.  
  
4.  Click **Apply** to add pairs to the **APPC Mode Properties: Partners** page while keeping the **Add Partnerships** dialog active.  
  
5.  When you finish selecting partnerships, click **OK** on the **Add Partnerships** dialog to return to the **APPC Mode Properties: Partners** page.  
  
6.  Click **OK** on the **APPC Mode Properties: Partners** page to commit the changes to the Host Integration Server configuration file.  
  
    > [!NOTE]
    >  You can select multiple modes for partnerships using the same LUs. Press the SHIFT key and the CTRL key and click to select non-contiguous modes.  
  
    > [!NOTE]
    >  The Host Integration Server configuration file is updated dynamically. There is no need to stop and restart SNA service.  
  
## APPC Mode Properties: Compression  
 **Maximum Send Compression**  
 Select the maximum compression desired from the drop down list. The valid values are: **None**, **Run Length Encoding (RLE)**, and **LZ9**. These options offer progressively better compression, but at a progressively higher CPU usage.  
  
 **Maximum Receive Compression**  
 Select the maximum compression desired from the drop down list. The valid values are: **None**, **Run Length Encoding (RLE)**, and **LZ9**. As with Maximum Send Compression, these options offer progressively better compression, but at a progressively higher CPU usage cost.  
  
 **Allow LZ and RLE Compression**  
 If LZ9 is used, this option controls whether data is compressed using RLE before being further compressed using LZ9.  
  
 **Endpoint Only Compression**  
 This option controls whether intermediate nodes may use compression if one of the endpoints does not support or otherwise does not use compression.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)