---
description: "Learn more about: Step 2: Configuring NLB on the Servers"
title: "Step 2: Configuring NLB on the Servers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 2: Configuring NLB on the Servers
After you have installed the base platform and configured the servers with the proper network settings (see [Step 1: Installing the Base Platform](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)), you may need to enable load balancing on BizTalk HTTP front-end servers and the BizTalk Messaging servers. This step is needed only if you have one or more BizTalk HTTP front-end servers installed on a separate computer from one or more BizTalk Messaging servers.  
  
 Load balancing ensures high-availability communication between the client computers (Internet Explorer users browsing to the MRSR site) and the MRSR servers, and between the MRSR servers and the messaging servers.  
  
 Load balancing on the **Public** interfaces of the HTTP front-end servers is required to enable the Intranet users to connect to the IIS Web servers on these computers. Load balancing on the **Private** interfaces of the HTTP front-end servers is required to enable the messaging servers to contact the web services on these computers.  
  
 On the messaging servers, assuming there are two servers, configure load balancing on the **Private** network adapters.  
  
 For more information, see the BizTalk Server Deployment Guide.
