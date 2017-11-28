---
title: "Resubmission Notes and Restrictions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 391064a9-1d61-4b10-97ab-d93b37d1ae23
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Resubmission Notes and Restrictions
The following notes and restrictions apply to the resubmission process:  
  
-   You can resubmit XML messages to the ESB WCF on-ramp, SOAP (ASMX) on-ramp, or any HTTP receive location.  
  
-   The default URL for the WCF on-ramp is http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc.  
  
-   The portal Web.config file defines the endpoint details for the WCF on-ramp in the **\<Client\>** node of the **\<System.ServiceModel\>** section. The following is the default value.  
  
    ```  
    <endpoint  
      address="http://localhost/ESB.ItineraryServices.WCF/ProcessItinerary.svc"  
      binding="wsHttpBinding"  
      bindingConfiguration="WSHttpBinding_ITwoWayAsyncVoid"  
      contract="ProcessRequest"   
      name="WSHttpBinding_ITwoWayAsyncVoid">                  
    </endpoint>  
    ```  
  
-   If the WCF on-ramp resides on a remote server, you must update the address to point to the correct server.  
  
-   The default URL for the SOAP (ASMX) on-ramp is http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx.  
  
-   The portal Web.config file defines the configuration for the SOAP (ASMX) on-ramp in the **\<applicationSettings\>** section. The following is the default value.  
  
    ```  
    <setting   
      name="Microsoft_Practices_ESB_Portal_ProcessItinerary_Process"  
      serializeAs="String">  
      <value>  
        http://localhost/ESB.ItineraryServices/ProcessItinerary.asmx  
      </value>  
    </setting>  
    ```  
  
-   If the ASMX on-ramp resides on a remote server, you need to update the URL with the correct server address.  
  
-   You can resubmit flat file formatted messages only to an HTTP receive location. You cannot submit them to a WCF or SOAP on-ramp. You must ensure that the HTTP receive location has the appropriate pipeline that can consume and/or parse the flat file.  
  
-   The resubmitted message does not contain any of the context properties of the original message.  
  
-   Resubmission applies to only the message body; it does not apply to the entire message.  
  
-   The resubmission process supports only single-part messages. You cannot use the resubmission process with multi-part messages.  
  
-   You cannot resubmit binary-formatted messages.