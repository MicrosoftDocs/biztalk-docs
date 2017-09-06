---
title: "Configuring HTTP Settings for Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ed400f1-561d-4812-adf1-20e4300fd048
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring HTTP Settings for Messages
As part of message-related HTTP settings, you can specify the properties expected by the Web server that receives AS2 messages.  
  
> [!IMPORTANT]
>  No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure message-related HTTP settings  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for Messages**.  
  
3.  Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.  
  
4.  Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.  
  
5.  Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.  
  
6.  Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)