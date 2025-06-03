---
description: "Learn more about: Known Issues with the POP3 Adapter"
title: "Known Issues with the POP3 Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-known-issue
---
# Known Issues with the POP3 Adapter
This section contains information that may help you avoid errors.  
  
## Known Issues  
  
#### The POP3 Adapter fails to process documents when running on a 64 bit operating system  
  
##### Problem  
 The POP3 Adapter will not process documents when running on a 64 bit operating system.  
  
##### Cause  
 The POP3 Adapter adapter handler is unable to run in a 64 bit host instance.  
  
##### Resolution  
 If you are running the POP3 Adapter on a 64 bit machine, configure the POP3 Adapter handlers to run in a 32 bit host. This option is available on the Host Properties page accessible from the BizTalk Administration console.  
  
## See Also  
 [Troubleshooting the POP3 Adapter](../core/troubleshooting-the-pop3-adapter.md)
