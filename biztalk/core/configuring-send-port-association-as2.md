---
description: "Learn more about: Configuring Send Port Association (AS2)"
title: "Configuring Send Port Association (AS2)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Send Port Association (AS2)
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses send port association to resolve an agreement for an outgoing AS2 message. An AS2 message is resolved to an agreement by matching the send port that subscribed to the message with the send port associated with an agreement. This topic provides instructions on how to associate send ports to an agreement.  
  
> [!IMPORTANT]
>  In BizTalk Server, the send port association is done only at the agreement level. However, in BizTalk Server 2009, the send ports were associated at the party level. For backward compatibility, a **Send Ports** page is also available as part of the party properties (see [Configuring General Party Properties (AS2)](../core/configuring-general-party-properties-as2.md)). Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well. However, the reverse is not true. You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.  
  
> [!IMPORTANT]
>  The send port association grid is disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
>   
>  The grid is disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the grid is disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure send port association  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, click **Send Ports**.  
  
3.  Click the empty cell under the **Name** column, and from the drop-down list, select the send port to associate with the agreement. The **URI** column displays the send port address.  
  
4.  To remove a send port association, select the row for a send port and click **Remove**.  
  
5.  To see the properties for a send port, select the row for a send port and click **Properties**.  
  
6.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md)
