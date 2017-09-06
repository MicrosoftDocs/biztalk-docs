---
title: "Configuring HTTP Settings for MDNs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c877e85-7887-43a9-9fd4-0853b573213f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring HTTP Settings for MDNs
As part of MDN-related HTTP settings, you can specify the properties expected by the Web server that receives the MDNs.  
  
> [!IMPORTANT]
>  All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
>   
>  The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure MDN-related HTTP settings  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for MDNs**.  
  
3.  Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.  
  
4.  Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.  
  
5.  Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.  
  
6.  Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)