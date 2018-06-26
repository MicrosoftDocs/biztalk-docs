---
title: "Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario
The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.  
  
Complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) before you begin this step.
  
## Add SWIFTNet configuration to the paramfile  
  
1. Open the paramfile in a text editor, such as Notepad.  
  
2. The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
3. In the paramfile, make the highlighted change to specify the Server Message partner name:  
    
    username:snlowner  
  
    subsystem_name:FileactStub  
  
    \#subsystem_group:fileactsnf  
  
    \#subsystem_dependency:Support,Swarm  
  
    subsystem_nature:critical  
  
    subsystem_start:  
  
    **spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact SnF\> -AdapterMode fileact"**  
  
    *END  
  
    subsystem_stop:  
  
    *KILL9:snlreceiver  
  
    *END  
  
    subsystem_status:  
  
    *NB:1:snlreceiver  
  
    *END  
  
    start_event:SNL001:subsystem FileactStubSnF is up  
  
    stop_event:SNL002:subsystem FileactStubSnF is down  
  
    \#subsystem_name:User  
  
    \##subsystem_group:user  
  
    \##subsystem_dependency:  
  
    \#subsystem_nature:critical  
  
    \#subsystem_start:  
  
    \#*END  
  
    \#subsystem_stop:  
  
    \#*END  
  
    \#subsystem_status:  
  
    \#*END  
  
    # start_event:SNL001:subsystem User is up  
  
    # stop_event:SNL002:subsystem User is down  
    
  
## Complete steps
 [FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)   
 [Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)