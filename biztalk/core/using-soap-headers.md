---
description: "Learn more about: Using SOAP Headers"
title: "Using SOAP Headers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Using SOAP Headers
Microsoft BizTalk Server provides support for defined and unknown SOAP headers. Defined SOAP headers are headers in the Web Service Description Language (WSDL) that are explicity stated in the Web service. Unknown SOAP headers are headers that in the WSDL that are not explicity stated in the Web service. For more information about using SOAP headers, see [SoapHeader Class](/dotnet/api/system.web.services.protocols.soapheader).

 BizTalk Server creates a context property for each defined SOAP header in the Web service.

> [!NOTE]
>  Consumed Web services support only defined SOAP headers.You cannot set unknown headers when consuming Web services.

## In This Section

-   [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)

-   [SOAP Headers with Published Web Services](../core/soap-headers-with-published-web-services.md)
