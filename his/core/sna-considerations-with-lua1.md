---
title: "SNA Considerations with LUA1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb8e9582-86b4-4367-8dbd-bd8856190a16
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNA Considerations with LUA
This section explains SNA information you need to consider when writing logical unit application (LUA) applications.  
  
## BIND checking  
 During initialization of the LU session, the host sends to the LUA application a BIND message that contains information such as request/response unit (RU) sizes for use by the LU session. Microsoft® Host Integration Server returns this message to the LUA application on [RUI_READ](./rui-read2.md). The LUA application must verify that the parameters specified on the BIND are suitable. The application has the following options:  
  
-   It can accept the BIND as it is, by issuing [RUI_WRITE](./rui-write2.md) containing an OK response to the BIND. No additional BIND data can be sent on the response.  
  
-   It can try to negotiate one or more BIND parameters. (This is only permitted if the BIND is negotiable.) To do this, the application issues **RUI_WRITE** containing an OK response, but including the modified BIND as data.  
  
-   It can reject the BIND by issuing **RUI_WRITE** containing a negative response, using an appropriate SNA sense code as data.  
  
     Validating the BIND parameters and ensuring that all messages sent are consistent with them is the responsibility of the LUA application. However, the following two restrictions apply:  
  
-   Host Integration Server rejects any **RUI_WRITE** that specifies an RU length greater than the size specified on the BIND.  
  
-   Host Integration Server requires the BIND to specify that the secondary LU is the contention winner and that error recovery is the responsibility of the contention loser.  
  
    > [!NOTE]
    >  For SLI, an application must specify that it will use [SLI_BIND_ROUTINE](./sli-bind-routine1.md) on the [SLI_OPEN](../core/sli-open2.md) if it will do any BIND checking.  
  
## Courtesy acknowledgments  
 Host Integration Server keeps a record of requests received from the host to correlate any response sent by the application with the appropriate request. When the application sends a response, Host Integration Server correlates the response with the data from the original request, and can then free the storage associated with it.  
  
 If the host specifies exception response only (a negative response can be sent but a positive response should not be sent), Host Integration Server must still keep a record of the request in case the application subsequently sends a negative response. If the application does not send a response, the storage associated with this request cannot be freed.  
  
 Because of this, Host Integration Server enables the LUA application to issue a positive response to an exception-response-only request from the host. (This is known as a courtesy acknowledgment.) The response is not sent to the host, but is used by LUA to clear the storage associated with the request.  
  
> [!NOTE]
>  The application does not need to send a courtesy acknowledgment for each exception-response-only request. For efficiency, the application can respond less frequently. The node treats a courtesy acknowledgment as an implicit acknowledgment for all prior pending requests.  
  
## Distinguishing SNA sense codes from other secondary return codes  
 A secondary return code that is not a sense code always contains a value of zero in its first two bytes.  
  
 An SNA sense code always contains a nonzero value in its first two bytes. The first byte gives the sense code category and the second identifies a particular sense code within that category. (The third and fourth bytes can contain additional information or can be zero.)  
  
## Information on SNA sense codes  
 If you need information about a returned sense code, see  
  
-   [Status-Error Message](../core/status-error-message1.md)  
  
-   [Error and Sense Codes](../core/error-and-sense-codes2.md)  
  
## Negative responses and SNA sense codes  
 SNA sense codes can be returned to an LUA application in the following cases:  
  
-   When the host sends a negative response to a request from the LUA application, it includes an SNA sense code indicating the reason for the negative response. This is reported to the application on a subsequent [RUI_READ](./rui-read2.md) or [SLI_RECEIVE](./sli-receive2.md) with the following information.  
  
    |Sense code|Description|  
    |----------------|-----------------|  
    |Primary return code|LUA_OK.|  
    |Request/response indicator, response type indicator, and sense data included indicator|All set to 1, indicating a negative response that includes sense data.|  
    |Data returned|The SNA sense code.|  
  
-   When Host Integration Server receives invalid data from the host, it generally sends a negative response to the host and does not pass the invalid data to the LUA application. This is reported to the application on a subsequent [RUI_READ](./rui-read2.md),[SLI_RECEIVE](./sli-receive2.md), [RUI_BID](./rui-bid1.md),or[SLI_BID](./sli-bid2.md) with the following information:  
  
    |Sense code|Description|  
    |----------------|-----------------|  
    |Primary return code|LUA_NEGATIVE_RESPONSE.|  
    |Secondary return code|The SNA sense code sent to the host.|  
  
-   In some cases, Host Integration Server detects that data supplied by the host is invalid, but cannot determine the correct sense code to send. In this case, it passes the invalid data in an exception request (EXR) to the LUA application on [RUI_READ](./rui-read2.md) or [SLI_RECEIVE](./sli-receive2.md) with the following information.  
  
    |Sense code|Description|  
    |----------------|-----------------|  
    |Request/response indicator|Set to 0, indicating a request.|  
    |Sense data included indicator|Set to 1, indicating that sense data is included. (This indicator is normally used only for a response.)|  
    |Message data|A suggested SNA sense code.|  
  
     The application must then send a negative response to the message. It can use the sense code suggested by Host Integration Server, or it can alter the sense code.  
  
-   Host Integration Server can send a sense code to the application to indicate that data supplied by the application was invalid. This is reported to the application on [RUI_WRITE](./rui-write2.md) or [SLI_SEND](./sli-send2.md) with the following information.  
  
    |Sense code|Description|  
    |----------------|-----------------|  
    |Primary return code|LUA_UNSUCCESSFUL.|  
    |Secondary return code|SNA sense code.|  
  
     The sense codes that can be returned as secondary return codes on LUA verbs are listed in the WINLUA.H header file. For this file, see the Host Integration Server or SNA SDK.  
  
## Pacing  
 Pacing is handled by the LUA interface. An LUA application does not need to control pacing and should never set the pacing indicator flag.  
  
 If pacing is being used on data sent from the LUA application to the host (determined by the BIND), [RUI_WRITE](./rui-write2.md) or [SLI_SEND](./sli-send2.md) may take some time to complete. This is because LUA has to wait for a pacing response from the host before it can send more data.  
  
 If an LUA application transfers large quantities of data in one direction, either to the host or from the host (for example, a file transfer application), the host configuration should specify that pacing is used in that direction. This ensures that the node receiving the data is not flooded with data and does not run out of data storage.  
  
## Purging data to end of chain  
 When the host sends a chain of request units to an LUA application, the application can wait until the last RU in the chain is received before sending a response, or it can send a negative response to an RU that is not the last in the chain. If a negative response is sent mid-chain, LUA purges all subsequent RUs from this chain and does not send them to the application.  
  
 When LUA receives the last RU in the chain, it indicates this to the application by setting the primary return code of [RUI_READ](./rui-read2.md) or [RUI_BID](./rui-bid1.md) to LUA_NEGATIVE_RESPONSE with a zero secondary return code.  
  
 The host can terminate the chain by sending a message such as CANCEL while in mid-chain. In this case, the CANCEL message is returned to the application on RUI_READ. The LUA_NEGATIVE_RESPONSE return code is not used.  
  
## Segmentation  
 Segmentation of RUs is handled by the LUA interface. LUA always passes complete RUs to the application, and the application should pass complete RUs to LUA.