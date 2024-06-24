---
description: "Learn more about: Step 2: Configure a Two-way WCF-WebHttp Send Port"
title: "Step 2: Configure a Two-way WCF-WebHttp Send Port"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 2: Configure a Two-way WCF-WebHttp Send Port
In this step you configure a two-way **WCF-WebHttp** send port to invoke the REST resource URL to retrieve delays in the US air carriers’ schedules.

### To configure WCF-WebHttp send port

1.  From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.

2.  On the **General** tab, do the following:

    |Use this|To do this|
    |--------------|----------------|
    |**Name**|Type **SendPortRESTAzureMarketPlace**.|
    |**Type**|Select **WCF-WebHttp**.|
    |**Send handler**|Select **BizTalkServerApplication**.|
    |**Send pipeline**|Select **PassThruTransmit**.|
    |**Receive pipeline**|Select **PassThruReceive**.|

     Click **Configure**.

3.  From the **WCF-WebHttp Transport Properties** dialog box, do the following:

    1.  On the **General** tab, for **Address (URI)**, enter `https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`.

    2.  On the General tab, for **HTTP Method and URL Mapping**, enter the following:

        ```
        <BtsHttpUrlMapping>
        <Operation Method="GET" Url="/On_Time_Performance" />
        </BtsHttpUrlMapping>

        ```

         Here, **GET** is the HTTP verb and **On_Time_Performance** is appended to the base URI to construct a unique resource URL to retrieve flight delays.

         > [!IMPORTANT]
         >
         > Within the URL field, you must "escape" any special XML characters to make sure that the port processes and 
         > preserves the special characters. For example, you must escape the `&` special character as `&amp;`.
         >
         > For the following text:
         > `Url="/Customer?{ID}&group={Location}"`
         >
         >
         > Use the following text instead: 
         > `Url="/Customer?{ID}&amp;group={Location}"`
         >
         > If the REST service also requires that you escape the special character within the URL used at runtime, you might have to use double-escaping.
         >
           >For:
           >`Url=”/Customer?{ID}&amp;group={Location}”`
           >
           >
           >Use:
           >`Url=”/Customer?{ID}&amp;amp;group={Location}”`

    3.  On the **Bindings** tab, for the **Maximum Received Message Size** field, select a sufficiently large value. That’s because typically the response message containing the flight status is considerably large and might exceed the default message size specified.

    4.  On the **Security** tab, do the following:

        1.  For the **Security mode**, select **Transport**.

        2.  For **Transport client credential type**, select **Basic**.

        3. Under the **User name credentials** box, select **Edit**.

        4. In the **Client Credentials** box, select **Do not use Single-Sign On**.

        5. Enter the username and password that you retrieved from the **My Account** tab after you signed in to [Microsoft Azure Marketplace](https://azuremarketplace.microsoft.com).
        
            The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.

        4.  Select **OK**.

    5.  On the **Messages** tab, for **Suppress Body for Verbs**, specify the verb for which you want to strip the message payload from the request message. For this tutorial, specify this as `GET`. Here’s why: A GET method call on the US Air Carrier flight delays REST endpoint does not require a message payload; the REST resource URL is sufficient to retrieve the information. However, to trigger the **WCF-WebHttp** send port that makes the REST call, you drop a dummy message that has some message body. The send port must not send that dummy message to the REST endpoint because, as explained earlier, the endpoint does not expect a message payload. So, before invoking the REST endpoint, the adapter strips the message payload from the dummy message only for the verbs that you specify in the **Suppress Body for Verbs** text box.

    6.  Click **OK** until you are back on the Send Port Properties dialog box. From the left pane, click **Filters**, and specify the filter to consume all messages that are received through the receive port you created in [Step 1: Configure a FILE Receive Location](../core/step-1-configure-a-file-receive-location.md).

        | Parameter | Value |
        |-|-|
        |**Property**|Set to **BTS.ReceivePortName**|
        |**Operator**|Set to **==**|
        |**Value**|Set to `ReceivePortRestAzureMarketPlace`|

    7.  Click **OK**.

## See Also
 [Tutorial 5: Invoking a REST Interface Using BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)
