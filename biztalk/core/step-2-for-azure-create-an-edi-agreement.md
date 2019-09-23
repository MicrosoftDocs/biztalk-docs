---
title: "Step 2 (For Azure): Create an EDI Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8003697-4955-45c0-ba0b-e7c293a050a2
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2 (For Azure): Create an EDI Agreement
In this topic, you will create partners using the Azure BizTalk portal available as part of the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. You will also create an agreement between the two partners (Northwind and Contoso) to process the X12 sales order message sent by Contoso to Northwind.

### To create partners

1.  Using your Microsoft account, log into the portal at [http://go.microsoft.com/fwlink/p/?LinkId=235056](https://go.microsoft.com/fwlink/p/?LinkId=235056).

2.  Create a partner for Northwind. Follow the steps at [Partners and Profiles](https://msdn.microsoft.com/library/windowsazure/hh689791) to create a partner.

    > [!IMPORTANT]
    >  Mark this partner as the managed partner.

3.  Repeat the steps to create a partner for Contoso. ***Do not*** mark this partner as a managed partner.

### To create an agreement

1.  In the portal home page, click **Agreements**.

2.  On the **Agreements** page, click the **X12** tab if you are not already on that tab. Then click **Create Agreement**.

3.  In the **New Agreement** page, enter the following details:

    |||
    |-|-|
    |**Field**|**Description**|
    |Name|Enter a name for the agreement. For this tutorial, specify the name as `DemoAgreement`.<br /><br /> **Note:** This is a mandatory field. The name for the agreement must be unique.|
    |Description|Enter notes or a description for the agreement.|
    |Partner 1 Profile (managed)|Select the managed partner for the agreement. A managed partner is a partner managed by the service provider and the pipelines are deployed for that partner during agreement deployment. Typically partners managed by service provider are configured as a managed partner while the enterprise partners are not marked as managed partners.<br /><br /> **Note:** For this tutorial, the managed partner is **Northwind**.<br /><br /> **Note:** The default profile is displayed in the Profile field. Choose the desired profile which has been configured for the partner.|
    |Partner 2 Profile|Select the partner for the agreement (who is not a managed partner).<br /><br /> **Note:** The default profile is displayed in the Profile field. Choose the desired profile which has been configured for the partner.|

     **Identities**

    |**Field**|**Description**|
    |---------------|---------------------|
    |Partner 1 ID Qualifier|Select an authenticating qualifier that provides unique business identities to the trading partners. For this tutorial, select **ZZ-Mutually Defined**.|
    |Value|Enter `Northwind`.|
    |Partner 2 ID Qualifier|Select an authenticating qualifier that provides unique business identities to the trading partners. For this tutorial, select **ZZ-Mutually Defined**.|
    |Value|Enter `Contoso`.|

     **Tracking**

    |**Field**|**Description**|
    |---------------|---------------------|
    |Track Send side message properties|Check this to store the message properties when the EDI message is sent to the partner. Once stored, you can query this data by clicking **Tracking** from the left pane on the Azure BizTalk Portal.<br /><br /> When enabled, you can also store the message body by checking **Track Send side message body**.|
    |Track Receive side message properties|Check this to store the message properties when the EDI message is received from a partner. Once stored, you can query this data by clicking **Tracking** from the left pane on the Azure BizTalk Portal.<br /><br /> When enabled, you can also store the message body by checking **Track Receive side message body**.|

4.  Click **Continue**.

     Clicking **Continue** adds two new tabs, one for receive settings and the other for send settings. Each tab is for a one-way agreement between the two partners, one for receiving messages and the other for sending messages.

5.  Specify the receive settings.

    1.  On the **Transport** page, set the **Transport type** to HTTP.

         The **Endpoint** field shows the URL to which Contoso must send the X12 sales order message.

    2.  On the **Protocol** page, specify the following values.

        1.  If required, specify values for ISA1, ISA2, ISA3, and ISA4.

        2.  Under **Acknowledgements**, select **TA1 expected** and **997 expected** if you want to generate technical and functional acknowledgements in response for receiving the message.

        3.  Under **Schemas**, click the **Upload** button and upload the **X12 840 schema** (you downloaded from [http://go.microsoft.com/fwlink/p/?LinkId=235057](https://go.microsoft.com/fwlink/p/?LinkId=235057)) and the **SalesOrder** schema (you created in [To create a schema within the EDI project](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateSchema)).

             Set the following properties under the **Schemas** section.

            |||
            |-|-|
            |Version|00401|
            |Transaction Type (ST1)|840|
            |Schema|/X12_00401_840.xsd|

    3.  On the **Transform** page, upload the transform you created in [To create a transform within the EDI project](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateTrfm).

         Under **Choose the maps you want to execute as part of this agreement**, choose **/X12_00401_840.xsd** for **Schemas** and **/EDI840TOSALESORDER.TRFM** for **Transform file name**.

    4.  On the **Route** page, select **Route to Service Bus Queue** and provide the relative address of the queue to which the message is sent. For this tutorial, specify the relative address as `queueordersedi` so that the complete URL is `https://<namespace>.servicebus.appfabriclabs.com/queueordersedi`.

        > [!NOTE]
        >  This tutorial does not cover the scenario where a failed message is sent to the endpoint you specify in the Message Suspension Settings. However, for successful deployment of the agreement, you must provide a value for this setting. You can enter a non-empty value.

6.  Specify the send settings.

    > [!NOTE]
    >  For the scenario described in this tutorial, you don’t need any send-side configuration for the agreement. However, an agreement cannot be deployed without specifying the send settings, even if they are dummy values. Also, On the **Send Settings** tab, you don’t need to provide any dummy values for **Inbound URI**, **Transform**, and **Batching**.

    1.  On the **Protocol** page, under **Schemas**, click the **Upload** button and upload the schema for the X12 840 message.

         Set the **Version** to **00401**, **Transaction Type** to **840**, and **Schema** to **X12_00401_840**.

    2.  On the **Transport** page, specify the endpoints where the response messages or acknowledgements will be sent to the partners. You must specify an endpoint each for the messages that are processed successfully as well as the messages that get suspended due to a failure in processing.

7.  Click **Deploy Agreement** to deploy the agreement. The agreement is now deployed at the URL that was displayed in the **Transport** page of the **Receive Settings** tab.

## See Also
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)