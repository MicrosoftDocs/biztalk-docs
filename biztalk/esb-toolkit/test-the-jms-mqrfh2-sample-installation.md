---
description: "Learn more about: Test the JMS MQRFH2 Sample Installation"
title: "Test the JMS MQRFH2 Sample Installation"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Test the JMS MQRFH2 Sample Installation
You can check for successful installation and operation of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] JMS MQRFH2 sample before you execute any of the sample scenarios.  
  
 **To test the JMS MQRFH2 sample installation**  
  
1.  Use the "RFHUtil" JMS test utility to write the test messages in the \Source\Samples\JMS\Test\Data\Load folder to the queue named ESB.JMS.SAMPLE.SENDTOBIZTALK.  
  
2.  The sample sends the message to the destination queue and a copy of the message to the reply queue.
