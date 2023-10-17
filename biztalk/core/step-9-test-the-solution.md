---
description: "Learn more about: Step 9: Test the Solution"
title: "Step 9: Test the Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df446ccc-add3-4dd3-b674-253dda385541
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Test the Solution
In this topic you test the hybrid application by sending a X12 840 sales order message to the HTTP endpoint where the EDI agreement is deployed. The sample sales order message looks like the following:

```
ISA*00*          *00*          *ZZ*CONTOSO        *ZZ*NORTHWIND      *991221*1226*U*00401*000000025*0*T*:~
GS*PO*THEM*US*19991221*1226*1*X*004010~
ST*840*0002~
BQT*00*BQT02*20120619*001*20120719~
PER*1A*John*EM*John@contoso.com~
N1*001~
N2*co~
N3*Contoso*One Contoso Way~
N4*Redmond*WA*98052*US~
PO1*PO101*121*01*10*AA*A1*1~
CTT*475~
SE*10*0002~
GE*1*1~
IEA*1*000000025~
```

 In this message, the highlighted segment (the line starting with **PO1**) contains the order quantity. The order quantity in this message is *121*. So, if you send this message, it must be inserted into the **SalesOrder** table. You can update the quantity to less than 100 and resend the message, it must then be sent to the file location you specified in the FILE send port.

 To send this message to the EDI agreement, you can use the **MessageSender** tool shipped with the samples for [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. You can download the samples from [https://go.microsoft.com/fwlink/p/?LinkId=235057](https://go.microsoft.com/fwlink/p/?LinkId=235057).

### To send a message

1.  Locate the **MessageSender** project in the sample package and build it.

2.  Use the resulting **MessageSender** command-line executable (under \bin\Debug folder within the project) to send messages to the deployed EDI agreement. This tool accepts command-line parameter in the following format:

    ```
    MessageSender.exe <ServiceBusNamespace> <IssuerName> <IssuerKey> <EDI agreement endpoint> <MessageFilepath> <ContentType>
    ```

     Where,

    |Parameter name|Description|
    |--------------------|-----------------|
    |ServiceBusNamespace|The Service Bus namespace|
    |IssuerName|Issuer Name for the specified namespace|
    |IssuerKey|Issuer Key for the specified namespace|
    |EDI agreement endpoint|The endpoint where the EDI agreement is deployed. You can get this endpoint URL from the Receive Settings tab (and within that, the Transport page) of the EDI agreement you deployed in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).|
    |MessageFilePath|Path to the file that contains the sample request message.|
    |ContentType|For this tutorial, set this parameter to **text/plain**.|

     Open a command prompt and navigate to the solution where you built the **MessageSender** project. Run the following command to send the request message with order quantity more than 100:

    ```
    MessageSender.exe <service bus namespace> owner <issuer key>https://<namespace>.servicebus.appfabriclabs.com/7576ff3d-a0f3-4a46-a4f6-f5be4a50616a/DemoAgreement<path to the sample message> "text/plain"
    ```

3.  Open SQL Server Management Studio, connect to the database that contains the **SalesOrder** table, and verify that a new record is inserted into the table. Notice the value in the **Qty** column; it must be *121*.

4.  Use **MessageSender** to send another message, but this time set the value of the quantity ordered in the message to *99*. You will notice that now, no record is inserted in the **SalesOrder** table. Instead, the message is copied to the file location you specified for receiving messages with order quantity less than 100. The received message resembles the following:

    ```
    <ns1:SalesOrder xmlns:ns0="http://schemas.microsoft.com/BizTalk/EDI/X12/2006" xmlns:ns1="http://ECommerceSalesOrder.Inbound">
      <CompanyCode>co</CompanyCode>
      <PartID>1</PartID>
      <Quantity>99</Quantity>
      <AskPrice>10</AskPrice>
      <RequestShipmentDate>2012-07-19</RequestShipmentDate>
      <Address>
        <Line1>Contoso</Line1>
        <Line2>One Contoso Way</Line2>
        <City>Redmond</City>
        <State>WA</State>
        <Country>US</Country>
        <Zipcode>98052</Zipcode>
      </Address>
      <Contact>
        <Firstname>John</Firstname>
        <Lastname>John@contoso.com</Lastname>
      </Contact>
      <Comments>Order from Partnerco</Comments>
      <DateNow>2012-06-19</DateNow>
    </ns1:SalesOrder>

    ```

     Notice the value in the **Quantity** element. It is *99*.

## See Also
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)
