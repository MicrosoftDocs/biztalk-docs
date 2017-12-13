---
title: "3270 LU Properties: General2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_LU_3270"
ms.assetid: 0e62f7b8-e92f-41ae-b76f-341758bf7917
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# 3270 LU Properties: General
## LU Number  
 **Enter the LU Number for LUs on 802.2, SDLC, or X.25.**  
 Enter an appropriate LU Number.  
  
 **LU Name**  
 Type the LU Name.  
  
 **Connection**  
 The connection for this LU is shown. The connection cannot be changed from this dialog box.  
  
 **Pool**  
 If the LU has already been assigned to a pool, the pool name appears here.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
 **Use Compression**  
 Select this option to enable 3270 LU data stream compression. This option must also be set in the host VTAM configuration for the LU.  
  
 **User Workstation Secured**  
 Select this option to enable a higher level of security. When the option is selected the user can only acquire an LU if:  
  
-   the user's User Record is assigned to this LU, and  
  
-   the user's workstation has been defined with a Workstation Definition.  
  
## 3270 Display LU Properties: Associated Printer LU  
 **Display LU**  
 Shows the display LU name if you have already created a display LU; otherwise, this will be filled in when you complete the configuration of this display LU.  
  
 **Associated Printer LU**  
 Click the DOWN arrow to display the list of available printer LUs on this connection. Choose a printer LU to associate with this display LU. If you have not created any printer LUs on this connection, you must do so before they will appear in the list.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)