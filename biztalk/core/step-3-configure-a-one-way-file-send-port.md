---
title: "Step 3: Configure a One-way FILE Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c52c6b6b-6f9c-48f2-8732-450fe3a15eae
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Configure a One-way FILE Send Port
In this step you configure a one-way FILE send port that consumes the response message received from the REST interface and copies it to a file location.  

### To configure a FILE send port  

1. From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. On the General tab, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Name**|Type **SendPortOutAzureMarketPlaceData**.|  
   |**Type**|Select **FILE**.|  
   |**Send handler**|Select **BizTalkServerApplication**.|  
   |**Send pipeline**|Select **PassThruTransmit**.|  

    Click **Configure**.  

3. From File Transport Properties, do the following:  


   |      Use this      |                                                              To do this                                                               |
   |--------------------|---------------------------------------------------------------------------------------------------------------------------------------|
   | **Receive folder** | Type a location where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies the response message. |
   |   **File name**    |                                                       Retain `%MessageID%.xml`                                                        |


4. On the **Filters** tab, specify the filter to consume all messages that are written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Message Box database by the receive port you created in [Step 2: Configure a Two-way WCF-WebHttp Send Port](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).  


   |              |                                       |
   |--------------|---------------------------------------|
   | **Property** |         Set to **BTS.SPName**         |
   | **Operator** |             Set to **==**             |
   |  **Value**   | Set to `SendPortRESTAzureMarketPlace` |


5. Click **OK**.  

## See Also  
 [Tutorial 5: Invoking a REST Interface Using BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)