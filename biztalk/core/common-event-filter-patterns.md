---
title: "Common Event Filter Patterns | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc80168b-25bd-4228-b84c-d38bf4e2fe4a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Common Event Filter Patterns
As you work with the BAM Interceptor for Windows Workflow Foundation (WF), you will likely notice that there are a set of common filter patterns that you will use frequently in your interceptor configuration files. While some of these filter patterns will be unique to your applications and environments, many patterns can be used across environments and in diverse applications.  
  
 This topic collects many of the common filter patterns used by interceptor configuration files written for WF applications. Patterns are grouped by Windows Workflow Foundation tracking event:  
  
- Activity status events  
  
- Workflow status events  
  
- User events  
  
  Each pattern can be copied into your interceptor configuration file and modified to suit your application.  
  
## Activity Status Event Filter Patterns  
 Activities are the fundamental building blocks of workflows. A workflow is a set of activities that are organized hierarchically in a tree structure. An activity represents an action in a workflow. It can be a simple action such as a delay, or it can be a composite activity that consists of several child activities.  
  
 The filters in this section filter activities and use one or more of the following BAM Interceptor for WF custom operations:  
  
-   GetActivityName  
  
-   GetActivityEvent  
  
-   GetActivityType  
  
-   GetActivityProperty  
  
-   GetWorkflowProperty  
  
-   GetContextProperty  
  
> [!NOTE]
>  If you do not use the GetActivityEvent operation in your filter, your filter will look for Closed activity events only.  
  
### Filter by Activity Name (Closed Activity)  
 You will frequently need to filter for closed activity events by activity name. This is useful when you need to capture data from a specific activity such as receiving a file or writing data to a database.  
  
 The fragment below filters for a closed activity named "MyActivity".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Type (Closed Activity Event)  
 There will be times when you want to filter an activity by type rather than name. For example, you may want to save activity name and a date/time stamp for all activities in a workflow. To accomplish this, you use the `GetActivityType` operation. `GetActivityType` compares a supplied type against the base type and all derived types to determine a match. Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Event (Any Activity Type)  
 This filter uses the GetActivityEvent operation to find closed activities. It is useful for capturing information about all closed events (versus a specific event by name or type).  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name and Type (Closed Activity Event)  
 You may choose to filter activities by activity name and activity type if you want to specify the exact type of activity (including processor architecture) that you are interested in finding. The sample below looks for "MyActivity" deriving from `System.Workflow.ComponentModel.Activity`; you can change this to a derived type to make it more restrictive.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
<ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name and Event (Any Activity Type)  
 This expression filters based on activity name and activity event. This is useful when you want to capture information for a specific activity and event or when capturing data from more than one activity event for a given activity. For example, you may want two different OnEvent elements, one for MyActivity when it is Executing and one for when it is Closed as shown below.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Type and Event  
 This filter is useful for capturing information about all activities that derive from a specific type during a single activity event. For example, you may be interested in tracking a purchase order ID and date/time stamp from a purchase order as it flows through a workflow. To accomplish this, you use the `GetActivityEvent` and the `GetActivityType` operations. `GetActivityType` compares a supplied type against the base type and all derived types to determine a match. Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name, Type, and Event  
 Filtering an activity by name, type and event can be useful when you want to better qualify the activity you are interested in tracking. For example, the filter below looks for the closed activity "MyActivity" that has a type that is equal to or derives from `System.Workflow.ComponentModel.Activity`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## Workflow Status Event Filter Patterns  
 The filters in this section filter workflow events and use one or more of the following BAM Interceptor for WF custom operations:  
  
-   GetWorkflowEvent  
  
-   GetContextProperty  
  
### Filter by Workflow Event  
 This expression filters by workflow event.  
  
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
  
## User Event Filter Patterns  
 If your application tracks custom information using the TrackData method, you can filter based on the characteristics of the data using one or more of the following BAM Interceptor for WF custom user data operations:  
  
- GetUserDataType  
  
- GetUserKey  
  
- GetUserData  
  
  The filter can combine these operations with the following to create a more complex expression:  
  
- GetActivityName  
  
- GetActivityType  
  
- GetActivityProperty  
  
- GetWorkflowProperty  
  
- GetContextProperty  
  
  If your filter does not include at least one user data operation, your filter will not be a user event filter and the enclosing OnEvent will cause an error (if a user operation appears in a corresponding update expression) or will be identified as an activity track point and not a user track point.  
  
### Filter by Activity Name and User Data Type  
 Frequently you can identify an event by activity name and user data type. The following expression filters for an activity named "MyActivity" and a user data type that derives from `System.Object`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Type and User Data Type  
 You can filter based on activity type and user data type. This grants you the latitude to filter events based on the type the derive from because both `GetActivityType` and `GetUserDataType` compare against the type specified and all derived types.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name, Activity Type, and User Data Type  
 This filter further restricts the activity type and user data type filter pattern by including activity name.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name and User Key  
 If your application has an activity that calls `TrackData` with a key determined at run time, you may want to filter by activity name and user key. This will enable you to trigger an `OnEvent` based on a specific key value. For example, your application might define multiple keys and dynamically select one within an activity.  
  
 The expression below filters for "MyActivity" containing a user key named "ItemKey".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Type and User Key  
 If your application contain multiple activities that call `TrackData` with a key determined at run time, you may want to filter by activity name and user key. This will enable you to trigger an `OnEvent` based on a specific key value. For example, your application might define multiple keys and dynamically select one within an activity.  
  
 The expression below filters for any activity deriving from `System.Workflow.ComponentModel.Activity` containing a user key named "ItemKey".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name, Activity Type, and User Key  
 This filter pattern further refines the activity type and user key filter pattern by including the activity name in the filter.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name, User Data Type, and User Key  
 This filter is useful when you want to restrict your filter to a named activity with a specific user key and deriving from a specific data type. For example, your activity may call TrackData using the key "Item" and a data value of string or integer depending upon the item type.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Type, User Data Type, and User Key  
 This filter is useful when you want to restrict your filter to an activity type with a specific user key and deriving from a specific data type. It can be more restrictive or less restrictive than using activity name, user data type, and user key based on the type used. If you specify the most-derived type, it could be more restrictive; if you specify the root base type, it could be less restrictive.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### Filter by Activity Name, Activity Type, User Data Type, and User Key  
 This filter further restricts the activity type, user data type, and user key pattern by the addition of activity name.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>   
```