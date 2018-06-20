---
title: "Tutorial 5: Invoking a REST Interface Using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73871ca3-abd0-45ae-b379-6df76a967a80
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 5: Invoking a REST Interface Using BizTalk Server
This section provides a step-by-step walkthrough on how to invoke a REST endpoint using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In this tutorial you invoke a REST endpoint available from the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace that returns the delays in flights of US air carriers. The tutorial uses the new **WCF-WebHttp** adapter introduced in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to invoke the REST endpoint.  
  
##  <a name="BKMK_Scenario"></a> Scenario Used in This Tutorial  
 [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace provides the following the REST resource URL to retrieve flight delays of US air carriers:  
  
```  
https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/On_Time_Performance  
```  
  
 If you enter this URL in the address bar of a Web browser, you are prompted for credentials to access the resource. After you have logged into the [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913), you can get the credentials from the **My Account** tab of the web page. The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.  
  
 In this tutorial, you use the resource URL and the credentials to configure a two-way **WCF-WebHttp** send port. The receive pipeline of the two-way send port receives the response message with the flight details and publishes the message to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message box database. You configure a FILE send port that subscribes to all the messages published by the WCF-WebHttp send port. The FILE send port consumes the message from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and copies it to a file location.  
  
 In a real-world business scenario, the WCF-WebHttp send port can be triggered by associating it with a larger business process such as a receive location that gets a message from a business application. However, in this tutorial, because the focus is on demonstrating how to invoke a REST interface, you can use a simple FILE location that receives a dummy message to trigger the send port.  
  
 So, to summarize, you must perform the following steps to configure this solution:  
  
1.  Configure a FILE receive location to pick a dummy request message.  
  
2.  Configure a two-way WCF-WebHttp send port to invoke the REST resource URL and receive a response.  
  
3.  Configure a one-way FILE send port to consume the response message with the flight details and copy it to a file location.  
  
## Set up Your [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace Account  
 To access the flight delay data exposed through the REST endpoint, you must first subscribe to the US Air Carrier Flight Delays sample data feed. Perform the following steps to do so:  
  
#### To subscribe to the data feed  
  
1. Log in to the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace using your Microsoft account.  
  
2. In the **Data** tab, locate and click the **US Air Carrier Flight Delays** service.  
  
3. On the data service page, click **Sign Up**. On the Sign Up page, accept the terms of agreement and then click **Sign up** again.  
  
4. In the **My Account** tab, retrieve the credentials to access the data service. The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels. You will need these credentials while configuring the **WCF-WebHttp** send port.  
  
## Set up Your Computer  
 To configure the scenario used in this tutorial you must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed and configured on your computer. If you want to provision a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer on a Windows Azure VM, follow the instructions at [Configuring BizTalk Server on an Azure VM](http://msdn.microsoft.com/library/azure/jj248689.aspx).  
  
## In This Section  
  
-   [Step 1: Configure a FILE Receive Location](../core/step-1-configure-a-file-receive-location.md)  
  
-   [Step 2: Configure a Two-way WCF-WebHttp Send Port](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md)  
  
-   [Step 3: Configure a One-way FILE Send Port](../core/step-3-configure-a-one-way-file-send-port.md)  
  
-   [Step 4: Test the Solution](../core/step-4-test-the-solution.md)