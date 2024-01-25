---
description: "Learn more about: Troubleshooting Resubmission Issues"
title: "Troubleshooting Resubmission Issues"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Troubleshooting Resubmission Issues
If you have problems resubmitting messages, check the following:  
  
-   Can you access the receive location through your browser? If you are trying to resubmit to the WCF on-ramp or the SOAP on-ramp, the URL should be of the form http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc or http://localhost/ESB.OnRampServices/ProcessItinerary.asmx. If you are trying to resubmit to an HTTP receive location, you can use your Internet browser to determine whether the receive location is functioning properly by appending a sample message to the query string, as shown in the following example.  
  
    ```  
    http://localhost/HTTPOnRamp/BTSHttpReceive.dll?<SampleMessage>Sample Message Content</SampleMessage>  
    ```  
  
-   Verify that the BizTalk HTTP receive adapter is properly configured.
