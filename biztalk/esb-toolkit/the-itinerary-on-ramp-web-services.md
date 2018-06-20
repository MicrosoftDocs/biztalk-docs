---
title: "The Itinerary On-Ramp Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7551974-b9d2-4ae3-b54c-3aa5ba058e95
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Itinerary On-Ramp Web Services
The Itinerary Web service is an itinerary on-ramp that exposes a method that allows clients to submit messages for processing by the Itinerary Service and then onward to the target Microsoft BizTalk or ESB operations.  
  
 The Itinerary Web service passes the payload to the ESB Itinerary pipeline components, which validates the itinerary to verify that these services are defined in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration. Then the component adds special context properties to the message containing the validated itinerary.  
  
 In the case of a generic itinerary on-ramp, a SOAP header containing an itinerary is not provided during message submission. Accordingly, the ESB Itinerary Selector pipeline component is used in place of the ESB Itinerary pipeline component. The ESB Itinerary Selector pipeline component resolves the itinerary based on a pre-defined resolver connection string, and it provides the same validation that the ESB Itinerary pipeline component provides.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes two variations of the Itinerary service to support both one-way and request-response message-exchange patterns. The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains an ASP.NET (ASMX) and a Windows Communication Foundation (WCF) version of both of these services, and it provides generic versions of the WCF services.  
  
 The names of the provided one-way itinerary services are **ESB.ItineraryService**, **ESB.ItineraryServices.WCF**, and **ESB.ItineraryServices.Generic.WCF**.  
  
 The names of the provided two-way itinerary services are **ESB.ItineraryServices.Response**, **ESB.ItineraryServices.Response.WCF**, and **ESB.ItineraryServices.Generic.Response.WCF**.  
  
 Each of the Itinerary Web services exposes the following methods:  
  
- **SubmitRequest**. For the ASMX-based service, this method takes an instance of the **XmlNode** class that contains the message to submit. For the WCF-based service, this method takes an XML string that contains the message to submit.  
  
- **SubmitRequestResponse**. For the ASMX-based service, this method takes a reference to an instance of the **XmlNode** class that contains the message to submit and returns the response message in the instance of the **XmlNode** passed to it. For the WCF-based service, this method takes a reference to an **Object** type that is an XML string that contains the message to submit and returns an array of **XmlNodes** in the **Object** that was passed to it.  
  
  For more information about using the Itinerary Web services, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).  
  
> [!NOTE]
>  By default, the Itinerary Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients. You should configure the service to require SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and the server that hosts the ESBExceptions database using a network-level IPSec and appropriate file-level access control list (ACL) permissions.