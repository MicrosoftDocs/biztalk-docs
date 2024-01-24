---
description: "Learn more about: Service Entries"
title: "Service Entries2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Service Entries
Each instance of a component appears to the system as a unique service. These services must be created using the Service Control Manager (SCM). The SCM creates a registry entry for each service under **SYSTEM\CurrentControlSet\Services**. This key contains all of the service-specific information.  
  
 The top-level service key contains information that the SCM uses to control the service. This includes the type of service that this key represents, how it should be started, what sort of error handling should be used, the path to the executable image, and so on. All information in this key should be handled by the SCM. Each service key also contains two subkeys—the Linkage key and the Parameters key.  
  
 The Linkage key is used by the Network Control Panel Applet to store binding information. The Parameters key contains information that is relevant to Host Integration Server Setup, such as the name of the DLL responsible for handling a link service. All information in this key should be handled by Host Integration Server Server Setup. The Parameters key contains another key, ExtraParameters, which is used for any IHV-specific information, including component-specific parameters and other information not required by the main SNA Server Setup program.
