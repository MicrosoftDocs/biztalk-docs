---
title: "Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4feec3f-4755-477e-b3d6-1dd6d075255e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario
The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.  
  
 Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).  
  
### To add SWIFTNet configuration to the paramfile  
  
1. Open the paramfile in a text editor, such as Notepad.  
  
   > [!NOTE]
   >  The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
2. In the paramfile, make the highlighted change to specify the Server Message partner name:  
  
    username:snlowner  
  
    subsystem_name:FileactStub  
  
    \#subsystem_group:fileact  
  
    \#subsystem_dependency:Support,Swarm  
  
    subsystem_nature:critical  
  
    subsystem_start:  
  
    **spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact RT \> -AdapterMode fileact"**  
  
    *END  
  
    subsystem_stop:  
  
    *KILL9:snlreceiver  
  
    *END  
  
    subsystem_status:  
  
    *NB:1:snlreceiver  
  
    *END  
  
    start_event:SNL001:subsystem FileactStub is up  
  
    stop_event:SNL002:subsystem FileactStub is down  
  
    \#subsystem_name:User  
  
    \##subsystem_group:user  
  
    \##subsystem_dependency:  
  
    \#subsystem_nature:critical  
  
    \#subsystem_start:  
  
    \#*END  
  
    \#subsystem_stop:  
  
    \#*END  
  
    \#subsystem_status:  
  
    # *END  
  
    # start_event:SNL001:subsystem User is up  
  
    # stop_event:SNL002:subsystem User is down  
  
## See Also  
 [FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)   
 [Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)