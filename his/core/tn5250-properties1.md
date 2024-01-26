---
description: "Learn more about: TN5250 Properties"
title: "TN5250 Properties1"
ms.custom: ""
ms.date: "01/26/2024"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_TN5250Service"
---
# TN5250 Properties
**Name**  
 Displays the name of the server running the TN5250 service. This field cannot be edited here.  
  
 **Comment**  
 Optionally, type a comment of up to 25 characters.  
  
 **Use Default**  
 Select **Use Default** to use the port number associated with telnet (as set in \\\DRIVERS\ETC\SERVICES).  
  
 **Use**  
 You can override the default value for a given server by selecting **Use** and typing another port number. You can also override this port number for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client computer to connect to multiple host computers.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
