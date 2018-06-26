---
title: "Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario
The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.  
  
 Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).  
  
### To add SWIFTNet configuration to the paramfile  
  
1. Open the paramfile in a text editor, such as Notepad.  
  
   > [!NOTE]
   >  The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.  
  
2. In the paramfile, make the highlighted change to specify the Server Message partner name:  
  
    username:snlowner  
  
    subsystem_name:InteractStub  
  
    \#subsystem_group:Interactsnf  
  
    \#subsystem_dependency:Support,Swarm  
  
    subsystem_nature:critical  
  
    subsystem_start:  
  
    **spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF\> -AdapterMode Interact"**  
  
    *END  
  
    subsystem_stop:  
  
    *KILL9:snlreceiver  
  
    *END  
  
    subsystem_status:  
  
    *NB:1:snlreceiver  
  
    *END  
  
    start_event:SNL001:subsystem InteractStubSnF is up  
  
    stop_event:SNL002:subsystem InteractStubSnF is down  
  
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
  
## See Also  
 [InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)   
 [Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)