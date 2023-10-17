---
description: "Learn more about: GetWorkflowEvent"
title: "GetWorkflowEvent | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2534e0b8-26df-4554-b0df-742014deb64d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetWorkflowEvent
Pushes the name of the current workflow event onto the stack.

## Syntax

```

<wf:Operation Name="GetWorkflowEvent" />
```

#### Parameters
 None.

## Pushed Value
 String containing the current workflow event.

## Remarks
 A workflow instance can pass through several states during the course of its execution. For example, a workflow instance may become idle, or it may be suspended. Every time the workflow instance changes state, it emits a workflow status event to the runtime tracking infrastructure. The Windows Workflow Foundation BAM interceptor supports most of the events defined by the `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent` enumeration, as shown in the following table.

|Activity event|Description|
|--------------------|-----------------|
|Changed|A workflow change has occurred on the workflow instance.|
|Completed|The workflow instance has completed.|
|Created|The workflow instance has been created.|
|Exception|An unhandled exception has occurred.|
|Idle|The workflow instance is idle.|
|Loaded|The workflow instance has been loaded into memory.|
|Persisted|The workflow instance has been persisted.|
|Resumed|A previously suspended workflow instance has resumed running.|
|Started|The workflow instance has been started.|
|Suspended|The workflow instance has been suspended.|
|Terminated|The workflow instance has been terminated.|
|Unloaded|The workflow instance has been unloaded from memory.|

> [!NOTE]
>  You cannot use both `GetWorkflowEvent` and `GetActivityEvent` in the same OnEvent element.

## Example
 The following sample contains a filter that is configured to find a specific activity—"FoodAndDrinksPolicy"—in a workflow. In the sample, a filter is configured to find the activity named "FoodAndDrinksPolicy" in a closed workflow. This is done by comparing the value returned by `GetWorkflowEvent` to the constant "Created".

```
<ic:Filter>
  <ic:Expression>
    <wf:Operation Name="GetWorkflowEvent" />
      <ic:Operation Name="Constant">
        <ic:Argument>Created</ic:Argument>
      </ic:Operation>
    <ic:Operation Name="Equals" />
  </ic:Expression>
</ic:Filter>
```

 This operation is useful for tracking the lifetime of a workflow and for detecting exceptions or other problems with the workflow.

## See Also
 [System.Workflow.Runtime.Tracking.TrackingWorkflowEvent enumeration](/dotnet/api/system.workflow.runtime.tracking.trackingworkflowevent)