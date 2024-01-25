---
description: "Learn more about: The ESB Exception API Members"
title: "The ESB Exception API Members"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The ESB Exception API Members
The **ESB.ExceptionHandling** assembly exposes public methods to create fault messages and to manage and retrieve them for processing, as described in the following table.  
  
|Member and use case|Description|  
|-------------------------|-----------------|  
|**CreateFaultMessage** [Exception handler scope]|**public static XLANGMessage CreateFaultMessage()** Takes no parameters. Returns an instance of the ESB fault message as an **XLANGMessage** instance populated with the current orchestration name, orchestration instance ID (a GUID), **System.Exception** instance, and other ambient properties. **Note:**  This Application Programming Interface (API) needs to be called only from an exception block within the XLANG.|  
|**AddMessage** [Exception handler scope]|**public static void AddMessage(faultMessage, existingMessage)** Takes as parameters two **XLANGMessage** instances; the first is a newly-created ESB fault message, and the second is any existing message instance in the orchestration. The method persists the existing message instance and its message context properties into the fault message and makes it available for retrieval using the **GetMessage** method. No return value.|  
|**SetException** [Exception handler scope]|**public static void SetException(faultMessage, exception)** Takes as parameters an ESB fault message as an **XLANGMessage** instance and **Exception** as an **Object** instance. The method persists the exception into the existing fault message and makes it available for retrieval using the **GetException** method. No return value.|  
|**GetMessage** [Subscriber/processor]|**public static XLANGMessage GetMessage(faultMessage, messageName)** Takes as parameters an ESB fault message received from a subscription as an **XLANGMessage** instance and the (**String**) name of the message previously added to the fault message (in the exception handler of the originating orchestration shape). Returns an **XLANGMessage** instance that matches the message name and that contains all the original context properties, including any custom promoted properties.|  
|**GetMessages** [Subscriber/processor]|**public static MessageCollection GetMessages(faultMessage)** Takes as the single parameter an ESB fault message received from a subscription as an **XLANGMessage** instance. Returns a **MessageCollection** instance populated with all the **XLANGMessage** instances previously added to the fault message (in the exception handler of the originating orchestration shape). Each **XLANGMessage** instance contains all the original context properties, including any custom promoted properties.|  
|**GetException** [Subscriber/processor]|**public static System.Exception GetException(faultMessage)** Takes as the single parameter a fault message received from a subscription as an **XLANGMessage** instance. Returns the **System.Exception** object previously added to the fault message (in the exception handler of the originating orchestration shape).|  
|**FaultSeverity** [Exception handler scope and subscriber/processor]|Public read/write property of the ESB fault message **XLANGMessage** class that exposes the severity of a fault message. A value from the **FaultCodes** enumeration: **Information** (0), **Warning** (1), **Error** (2), **Severe** (3), or **Critical** (4).|  
|**MessageCollection** [Subscriber/processor]|A collection of the messages returned by the **GetMessages** method. This class derives from **ArrayList** and implements an enumerator to allow iteration using the **MoveNext** method.|
