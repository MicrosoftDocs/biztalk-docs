---
description: "Learn more about: ADAPTERCOUNTER"
title: "ADAPTERCOUNTER2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ADAPTERCOUNTER
The **ADAPTERCOUNTER** structure represents an individual SNA Perfmon event that can be monitored, such as the total bytes transmitted. All of the data needed to display a single Perfmon event is stored in this structure.  
  
## Syntax  
  
```  
  
typedef struct adaptercounter  
{  
    ULONG count;  
    ULONG type;  
    LONG scale;  
} ADAPTERCOUNTER;   
```  
  
## Members  
 **count**  
 The count for a specific Perfmon event since startup of the link service. Each time a Perfmon event takes place, the count is incremented accordingly, based on the type of event being counted. This count is maintained by the link service.  
  
 **type**  
 The event type that is being monitored with this **ADAPTERCOUNTER**. The **type** member instructs Perfmon whether the **count** member represents a numeric counter such as number of connection failures, a rate such as throughput in bytes transferred per second, or a percentage. For suitable values, see the platform SDK documentation of **PERF_COUNTER_\\*** (for example, **PERF_COUNTER_COUNTER** or **PERF_COUNTER_RAWCOUNT**).  
  
 **scale**  
 The default scale to be used by the Perfmon application when displaying this event. The **count** member is scaled by 10 raised to the power of scale such that a scale member of –1 multiplies **count** by 0.1.
