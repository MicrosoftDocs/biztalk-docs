---
title: "Step 4: Create the Receive Port for Accepting ADT Query Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, receive ports"
ms.assetid: 8bef032f-5f43-4d36-b88f-ed81f27bb803
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Create the Receive Port for Accepting ADT Query Messages
You create a receive port to specify the location for incoming query messages sent by the Admissions, Discharge, and Transfer (ADT) system. Use the following procedure to create the receive port for accepting queries (QRY^Q01 messages) from the ADT system using the Minimal Lower Layer Protocol (MLLP) adapter.  

## Create the ADT_ReceivePort receive port  

1. Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  

2. Right-click **Receive Ports**, select **New**, and then select **Request Response Receive Port**.  

3. For the **Name**, enter **ADT_ReceivePort**.  

4. Select **Apply** to bind the port, and then select **Receive Locations**.  

5. Select **New**. 

6. For the **Name**, enter **ADT_Receive**.  

7. In the **Transport** section, select **Type**, and then select **MLLP** from the drop-down list.  

8. Select **Configure**. In **MLLP Transport Properties**, configure the following, and then select **OK**.  


   |           Use this           |                                                                                                                                                                                                     To do this                                                                                                                                                                                                     |
   |------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Connect retry time (sec)** |                                                                 New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>The upper limit of time to wait before attempting to reconnect a dropped or closed connection. Applicable when **Connection Initiated by** is set to **Local**.<br/><br/>Default is 20 seconds.                                                                  |
   | **Connection initiated by**  | New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter **Local** for the MLLP receive location to initiate the connection to a remote LOB server. This is the new option.<br/><br/>Enter **Remote** for the MLLP receive location to continue to listen for a connection from the remote LOB server. This is the backwards-compatible default option.<br/><br/>Default is Remote. |
   |     **Connection Name**      |                                                                                                                                                                                             Enter **ADT_ReceiveMLLP**.                                                                                                                                                                                             |
   |        **Host name**         |                                                                                                                                              Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions. <br/><br/>Enter **localhost**.                                                                                                                                               |
   |     **Local Host name**      |                                                                            New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the DNS name or IP address of the local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. You can also enter **localhost**.                                                                             |
   |           **Port**           |                                                                                                                                                Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions. <br/><br/>Set to **22000**.                                                                                                                                                |
   |        **Local Port**        |                                                                                       New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the TCP port number for the LocalHost connection. Applicable only when **Connection Initiated by** is **Remote**. <br/><br/>Set to **22000**.                                                                                        |
   |       **Remote Host**        |                                                                                                   New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the DNS name or IP address of the remote LOB server. Applicable when **Connection Initiated by** is set to **Local**.                                                                                                    |
   |       **Remote Port**        |                                                                                      New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the TCP port number for the remote host connection. Applicable when **Connection Initiated by** is set to **Local**.<br/><br/>Set to **22000**.                                                                                       |


9. Set the **Receive Handler** to **BizTalkServerApplication**.  

10. Set the **Receive Pipeline** to **BTAHL72XPipelines.BTAHL72XReceivePipeline**.  

11. Set the **Send pipeline** to **PassThruTransmit**.

12. Select **OK** to save your changes.  

13. Enable the receive location you just created by right-clicking it, and then select **Enable**.  

## Next step  
[Step 5: Create the Receive Port for Accepting HIS Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)