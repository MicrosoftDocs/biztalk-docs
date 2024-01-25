---
description: "Learn more about: GetActivityEvent"
title: "GetActivityEvent"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetActivityEvent
Pushes the name of the current activity event onto the stack.

## Syntax

```

<wf:Operation Name="GetActivityEvent"/>
```

#### Parameters
 None.

## Pushed Value
 String containing the current activity event.

## Remarks
 A workflow activity can pass through several states during the lifetime of the workflow. The Windows Workflow Foundation BAM interceptor supports most of the execution status values defined by the `System.Workflow.ComponentModel.ActivityExecutionStatus` enumeration, as shown in the following table.

|Execution status|Description|
|----------------------|-----------------|
|Canceling|Represents the status when an activity is in the process of being canceled.|
|Closed|Represents the status when an activity is closed.|
|Compensating|Represents the status when an activity is compensating.|
|Executing|Represents the status when an activity is executing.|
|Faulting|Represents the status when an activity is faulting.|

> [!NOTE]
>  You cannot use both `GetActivityEvent` and `GetWorkflowEvent` in the same OnEvent element.

## Example
 The following sample contains an event filter expression configured to find a specific activity—FoodAndDringPolicy—in a Closed workflow. This is done by using a combination of operations including `GetActivityEvent`, `GetActivityName`, and logical operations.

```
<ic:Filter>
  <ic:Expression>
    <wf:Operation Name="GetActivityName"/>
    <ic:Operation Name="Constant">
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>
    </ic:Operation>
    <ic:Operation Name="Equals"/>
    <wf:Operation Name="GetActivityEvent"/>
    <ic:Operation Name="Constant">
      <ic:Argument>Closed</ic:Argument>
    </ic:Operation>
    <ic:Operation Name="Equals"/>
    <ic:Operation Name="And"/>
  </ic:Expression>
</ic:Filter>
```

 This filter pattern is common with Windows Workflow Foundation interceptor configuration files.

> [!NOTE]
>  Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.

## See Also
 [System.Workflow.ComponentModel.ActivityExecutionStatus enumeration](https://go.microsoft.com/fwlink/?LinkId=119570)
