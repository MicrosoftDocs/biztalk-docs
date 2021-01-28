---
description: "Learn more about: How to Create Role Links in Orchestrations"
title: "How to Create Role Links in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc386ac2-a851-4342-9ceb-0b6faddf4ece
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Role Links in Orchestrations
The following are the basic tasks you will need to complete to use role links in your orchestration:

-   Create parties and send ports and associate them with each other.

-   Use the following procedure to create role link types and add the port types.

    |To create a role link type|
    |--------------------------------|
    |1.  In the Orchestration View window, expand **Types**, right-click **Role Link Types**, and then click **New Role Link Type**.<br />2.  Click the role link type you just created. In the Properties window, in the **Identifier** field, type `Provider_Consumer_RoleLinkType`.<br />3.  Expand **Provider_Consumer_RoleLinkType**, and then click **Role_1**. In the Properties window, in the **Identifier** field, type `ConsumerRole`.<br />4.  Right-click **ConsumerRole**, and then click **Add Port Type**. This starts the Port Type Wizard.<br />5.  On the **Welcome to the Port Type Wizard** page, click **Next**.<br />6.  On the **Select a Port Type or create a new Port Type** page, select **Create a new Port Type**, and then for **Port Type Name**, type `ConsumerPortType`.<br />7.  For **Communication Pattern**, select **One-Way**, and for **Access Restrictions**, select **Public - no limit**. Click **Next**.<br />8.  On the **Completing the Port Wizard** page, click **Finish**.<br />9. Right-click **Provider_Consumer_RoleLinkType**, and then click **New Role**.<br />10. Click **Role_1**, and then in the Properties window, in the **Identifier** field, type `ProviderRole`.<br />11. Right-click **ProviderRole**, and then click **Add Port Type**. This starts the Port Type Wizard.<br />12. On the **Welcome to the Port Type Wizard** page, click **Next**.<br />13. On the **Select a Port Type or create a new Port Type** page, select **Create a new Port Type**, and then for **Port Type Name**, type `ProviderPortType`.<br />14. For **Communication Pattern**, select **One-Way**, and for **Access Restrictions**, select **Public - no limit**. Click **Next**.<br />15. On the **Completing the Port Wizard** page, click **Finish**. **Note:**      Configured ports placed inside of role links do not retain their associated binding information.|

     In the preceding procedure, you create a role link type that contains two roles—a ProviderRole that will receive and process messages from the consumer and a ConsumerRole that your orchestration will use the send port provided with the role to send messages to the consumer.

> [!NOTE]
>  The role link type can contain a provider role and a consumer role, and it can include one of either or one of each, depending on your business process needs.

-   Use the following procedure to add role links to your orchestration.

    |To create a role link by using the Role Link Wizard|
    |---------------------------------------------------------|
    |1.  In the orchestration Toolbox, drag the **Role Link** shape to the design surface. This starts the Role Link Wizard.<br />2.  On the **Welcome to the Role Link Wizard** page, click **Next**.<br />3.  On the **Role Link Name** page, in the **Name** field, type `Provider_Consumer`. Click **Next**.<br />4.  On the **Role Link Type** page, select **Use an existing Role Link Type**. In the **Role Link Type Name** drop-down list, select **Provider_Consumer_RoleLinkType**. Click **Next**.<br />5.  On the **Role Identification** page, select **ProviderRole** from the **Which role will this orchestration implement to receive and process messages from partners?** drop-down list. The wizard automatically selects **ConsumerRole** for **This orchestration will use the role below to send messages to partners on ports inside the role**. Click **Next**.<br />6.  On the **Role Link Usage** page, select **I will be sending the first message to my partner's role**. Click **Finish**.|

     In the preceding procedure, you further define the ConsumerRole as the initiating role. This means that your orchestration will send the first message to the consumer through the port provided by the ConsumerRole and then the ProviderRole will receive the message sent back from the consumer for further processing.

    > [!NOTE]
    >  If there is only one role in the role link type, you need to define your role in the business process by selecting either **Provider Role: I will be receiving the first message** or **Consumer Role: I will be sending the first message** instead of performing step 5 in the preceding procedure.

-   Design your business process. You can leverage correlation sets to ensure that an incoming message matches the appropriate instance of an orchestration.

-   Associate the ports with **Send** and **Receive** shapes. In addition, do the following:

    -   If the initiating role is a consumer for sending messages, explicitly set the **DestinationParty** property (once and only once) in your orchestration. To do so, set the value of the **DestinationParty** in the **Expression** shape, as in the following example, where ConfirmOrder is the name of a role link, and PartnerName and OrganizationName are parameters of a party:

        ```
        ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");
        ```

    -   If the initiating role is a provider for receiving messages, the **DestinationParty** property is initialized automatically by the receiver. The **DestinationParty** is set to the provider itself. The **SourceParty** property is read-only, and is supplied through a trusted pipeline component to resolve the party name based on the security identifier (SID) of the sender or on a certificate associated with the party. The host running the pipeline component must be marked as **Authentication Trusted**. You can get the value of the **SourceParty** in the **Expression** shape by using the following sample code:

        ```
        PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);
        ```

## Examples of Using Role Links

-   [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md)

-   Download the SDK sample "Using Role Links" from the BizTalk Server code samples available at [https://go.microsoft.com/fwlink/?LinkId=73703](https://go.microsoft.com/fwlink/?LinkId=73703).

## See Also
 [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md)
 [How to Use the Role Link Shape](../core/how-to-use-the-role-link-shape.md)
 [How to Use the Role Link Wizard](../core/how-to-use-the-role-link-wizard.md)
